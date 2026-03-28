---
name: resume-linkedin-optimiser
description: >-
  Use this skill when the user wants to optimise their resume or LinkedIn profile.
  Trigger on "optimise my resume", "tailor my resume", "resume for [company]",
  "update my LinkedIn", "LinkedIn optimisation", "create a resume", "generate a resume",
  "ATS optimise", "resume review", "help with my resume", "LinkedIn headline",
  "LinkedIn profile review", or any request to generate, tailor, or optimise a resume
  or LinkedIn profile for a specific role.
---

# Resume & LinkedIn Optimiser

Generate an ATS-optimised, story-seeded resume and/or optimised LinkedIn profile
recommendations from the user's career knowledge base, existing resume, and a target
job description. Every bullet is a compressed version of a story designed to invite
interview questions about the user's strongest achievements.

## Required Inputs

- **Target job description** (required): The JD for the role they're applying to. User can paste it or provide a URL.

## Optional Inputs

- **Existing resume**: File path to current resume (markdown, .txt, .docx, or PDF)
- **Career knowledge base**: File path to structured career KB (from `/career-kb-builder`)
- **Existing LinkedIn profile URL**: For analysis and recommendations
- **Raw contribution notes**: Unstructured notes about recent work the user wants to incorporate

## Step 1: Read the base guide

Read the reference guide bundled with this plugin. Find it locally or fetch from GitHub:

```bash
# Find locally
find ~/.claude -name "resume-linkedin-optimiser-guide.md" -path "*/resume-linkedin-optimiser/*" 2>/dev/null | head -1

# Fallback: fetch from GitHub
gh api repos/Avengers-au/claude-skills/contents/plugins/resume-linkedin-optimiser/reference/resume-linkedin-optimiser-guide.md --jq '.content' | base64 -d
```

This contains ATS rules, action verbs, LinkedIn algorithm mechanics, story seeding
technique, and the tailoring process. Follow it precisely.

## Step 2: Gather inputs

### Career Knowledge Base
Look for the user's career KB:

```bash
find . -name "career-knowledge-base.md" -o -name "career-kb.md" -o -name "story-bank.md" 2>/dev/null | head -5
```

If found, read it — this is the primary source of achievement data.

### Existing Resume
If the user provides a resume file, read it to understand current positioning.

### Job Description
If the user provides a URL, fetch it with `WebFetch`. Otherwise, they'll paste it directly.

### Raw Notes
If the user has unstructured notes about recent contributions, read those too. Extract achievements and metrics using the quantification techniques from the career KB guide.

## Step 3: Analyse the job description

Extract from the JD:

1. **Required skills and technologies** — listed explicitly
2. **Preferred/nice-to-have skills** — secondary keywords
3. **Key responsibilities** — what the role does daily
4. **Level signals** — scope, team size, impact expectations
5. **Company values** — if mentioned, these influence language
6. **Priority order** — skills/responsibilities listed first are weighted higher

Create a keyword map:

```
Primary keywords: [skill1, skill2, skill3] — must appear in resume
Secondary keywords: [skill4, skill5] — include if the user has them
Value language: [phrases from the JD to mirror]
```

## Step 4: Select and tailor stories

From the career KB (or existing resume + raw notes), select the strongest stories:

1. **Match stories to JD keywords** — prioritise stories whose competency tags and tech stack overlap with the JD
2. **Select 3-5 bullets per role** — most relevant to THIS job first
3. **Pull or create `resume_bullet`** — compressed 1-2 line version with hook and quantified result
4. **Apply action verb upgrades** — replace weak verbs ("Worked on", "Helped") with strong verbs from the guide
5. **Mirror JD language** — use the exact phrasing from the JD where natural

## Step 5: Generate the resume

Write a tailored resume as a local markdown file. Follow this structure:

```markdown
# [Full Name]
[Email] | [Phone] | [Location] | [LinkedIn URL] | [GitHub URL]

## Summary
[2-3 lines: strongest value proposition tailored to THIS role. Include 2-3 metrics.
Mirror language from the JD.]

## Experience

### [Company Name] — [Title]
**[Start Date — End Date]**

- [Story-seeded bullet with quantified result]
- [Story-seeded bullet with quantified result]
- [Story-seeded bullet with quantified result]

### [Previous Company] — [Title]
**[Start Date — End Date]**

- [Story-seeded bullet]
- [Story-seeded bullet]

## Skills

**Languages & Frameworks:** [ordered by JD priority]
**Infrastructure & Tools:** [ordered by JD priority]
**Practices:** [ordered by JD priority]

## Education

**[Degree]** — [University] ([Year])
```

**Output path:** `./resume-[company-name]-[date].md`

## Step 6: Generate LinkedIn recommendations (if requested)

If the user wants LinkedIn optimisation, produce a recommendations document:

```markdown
# LinkedIn Profile Optimisation: [Target Role]

## Headline (current → recommended)
Current: "[their current headline]"
Recommended: "[R-S-I-C formula: Role | Speciality | Impact]"

## About Section (recommended)
[Full About section text: hook + narrative + current focus + specialties]

## Experience Updates
### [Company] — [Role]
[Recommended bullet updates using linkedin_version from career KB]

## Skills to Add/Reorder
1. [Skill matching JD] — move to top 3
2. [Skill matching JD] — add if missing
...

## Other Recommendations
- [Open to Work setting recommendation]
- [Engagement strategy]
- [Profile completeness gaps]
```

**Output path:** `./linkedin-recommendations-[date].md`

## Step 7: Quality checks

After generating, verify:

### Resume Checks
- [ ] No tables, columns, graphics, or images
- [ ] Standard section headings ("Experience", "Education", "Skills")
- [ ] Contact info in body, not header/footer
- [ ] Consistent date formatting throughout
- [ ] Every bullet starts with a strong action verb
- [ ] Every bullet has a quantified result
- [ ] JD primary keywords appear 1-3 times each
- [ ] Both acronyms and full forms included (e.g., "CI/CD (Continuous Integration/Continuous Deployment)")
- [ ] Length appropriate for experience level (1 page for <5 years, 1-2 for 5-10, 2 for 10+)
- [ ] Every bullet corresponds to a story the user can deliver in 2-3 minutes

### LinkedIn Checks
- [ ] Headline under 120 characters, front-loaded with important keywords
- [ ] About section hook visible before "see more" fold
- [ ] Top 3 skills match target role keywords
- [ ] Experience bullets include quantified achievements

Report results to the user with specific items to review.

## Rules

1. **Every bullet must be story-seeded.** No duty descriptions. Every line should invite "Tell me more about that" and correspond to a deliverable CARL story.
2. **Mirror JD language naturally.** Use their exact phrases where it doesn't feel forced. "Collaborate cross-functionally" if they say that, not "worked with other teams."
3. **Keywords 1-3 times max.** More is stuffing and modern ATS penalises it.
4. **Strong verbs only.** Architected, Spearheaded, Optimised, Pioneered. Never "Responsible for," "Worked on," "Assisted."
5. **Quantify everything.** Use estimation techniques if exact numbers aren't available. "Approximately 40%" is better than nothing.
6. **ATS-safe formatting.** No tables, no columns, no graphics. Standard section headings. .docx or clean markdown.
7. **Output locally.** Write to the current working directory. Resume and LinkedIn docs are personal — don't create gists or commit to repos.
8. **Preserve the user's voice.** The resume should sound like them, not like a template. If they naturally use certain phrases or framing, keep it.
9. **Include both acronyms and full forms.** "AWS (Amazon Web Services)", "CI/CD (Continuous Integration/Continuous Deployment)."
10. **R-S-I-C for LinkedIn headlines.** Role | Speciality | Impact/Value. Under 120 characters. Front-load important keywords.
