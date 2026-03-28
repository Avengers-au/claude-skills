---
name: salary-negotiation-playbook
description: >-
  Use this skill when the user wants to prepare for salary or compensation negotiation.
  Trigger on "salary negotiation", "negotiate my offer", "comp negotiation",
  "negotiate compensation", "I got an offer from [company]", "how much should I ask for",
  "counter offer", "salary research for [role]", "what should I be paid",
  "negotiate equity", "RSU valuation", or any request to research market rates
  or generate a personalised negotiation strategy for a specific offer.
---

# Salary & Compensation Negotiation Playbook Generator

Generate a personalised compensation negotiation strategy backed by live market research.
Conducts real-time salary research using multiple data sources (Levels.fyi, Glassdoor,
Hays, SEEK + salary-seeker for AU roles), analyses the specific offer structure, and
produces a tactical negotiation playbook with scripts, counter-offer strategies, and
company-specific patterns.

## Required Inputs

- **Company name** (required)
- **Offer details OR role being applied to** (required): Either the specific offer (base, equity, signing, bonus) or the role they're researching pre-offer

## Optional Inputs

- **Role title and level**: e.g., "Senior SWE, L5"
- **Location**: Critical for AU vs US comp differences and tax
- **Competing offers**: Details of other offers for leverage analysis
- **Current compensation**: For calculating improvement
- **SEEK job ID**: If AU role, enables salary-seeker extraction
- **Equity details**: RSUs, options, vesting, strike price

## Step 1: Read the base guide

Read the reference playbook bundled with this plugin. Find it locally or fetch from GitHub:

```bash
# Find locally
find ~/.claude -name "salary-negotiation-playbook.md" -path "*/salary-negotiation-playbook/*" 2>/dev/null | head -1

# Fallback: fetch from GitHub
gh api repos/Avengers-au/claude-skills/contents/plugins/salary-negotiation-playbook/reference/salary-negotiation-playbook.md --jq '.content' | base64 -d
```

This contains comp anatomy, negotiation psychology, scripts, company patterns, AU specifics,
and equity valuation. Use as foundation — supplement with live research.

## Step 2: LIVE market research (MANDATORY)

### For ALL roles:

1. **Levels.fyi** — Search: `WebSearch "[company] [role] [level] levels.fyi compensation"`. Extract TC range for the specific company + level + location
2. **Glassdoor** — Search: `WebSearch "[company] [role] salary glassdoor [location]"`. Note the range and sample size
3. **Blind** — Search: `WebSearch "[company] [role] TC blind"`. Look for recent data points
4. **H1B data** (if US company) — Search: `WebSearch "[company] [role] h1bdata.info"`. Government-mandated base salary disclosure

### For Australian roles specifically:

5. **salary-seeker** — If the user has a SEEK job ID:
```bash
# Clone if not already present
git clone https://github.com/b3n-j4m1n/salary-seeker.git /tmp/salary-seeker 2>/dev/null
# Run salary extraction
bash /tmp/salary-seeker/salary-seeker.sh [SEEK_JOB_ID]
```
If no SEEK job ID, search for the role on SEEK and extract one from the URL.

6. **Hays Salary Guide** — Search: `WebSearch "hays salary guide [role] [city] australia [year]"`. Most comprehensive AU data
7. **Robert Half** — Search: `WebSearch "robert half salary guide [role] australia technology"`. Three-percentile data
8. **SEEK** — Search: `WebSearch "seek salary [role] [city]"`. Advertised ranges

### Research the company's negotiation patterns:

9. **Company negotiation intelligence** — Search: `WebSearch "[company] salary negotiation [year]"` on interviewing.io, Candor, Glassdoor. Look for: how flexible they are, which components are negotiable, known tactics (Meta lowball, Apple tight on base, Amazon back-loaded vesting)

## Step 3: Analyse the offer (if provided)

Break down the offer into components and compare each to market:

```markdown
## Offer Analysis

| Component | Offered | Market P25 | Market P50 | Market P75 | Assessment |
|-----------|---------|-----------|-----------|-----------|------------|
| Base | $[X] | $[X] | $[X] | $[X] | Below/At/Above market |
| Equity (annualised) | $[X] | $[X] | $[X] | $[X] | ... |
| Signing bonus | $[X] | $[X] | $[X] | $[X] | ... |
| Annual bonus | $[X] | $[X] | $[X] | $[X] | ... |
| **Total Year 1** | **$[X]** | **$[X]** | **$[X]** | **$[X]** | ... |
| **Annualised 4-year TC** | **$[X]** | ... | ... | ... | ... |
```

For AU offers, additionally check:
- Is the salary "plus super" or "package including super"?
- What is the effective tax rate on each component?
- How are RSUs taxed under Division 83A?

## Step 4: Generate the negotiation playbook

Write to temp and create a gist:

1. Write: `/tmp/salary-negotiation-[company].md`
2. Gist: `gh gist create /tmp/salary-negotiation-[company].md -d "Salary Negotiation: [Company] — [Role]"`
3. Clipboard: `echo "$URL" | pbcopy 2>/dev/null`
4. Return URL

### Playbook structure

```markdown
# Salary Negotiation Playbook: [Company] — [Role] ([Level])

## Market Research Summary
[Data from all sources researched. Include specific data points with source attribution.
Show the range (P25/P50/P75) for this company + level + location.]

### salary-seeker Results (AU only)
[If SEEK job ID was provided: the extracted hidden salary range]

## Offer Analysis
[Component-by-component breakdown vs market. Clear assessment of where the offer sits.]

## Company-Specific Intelligence
[From the base guide + live research: how this company negotiates, which components
are flexible, known tactics, who has authority, what leverage works.]

## Negotiation Strategy

### Your BATNA
[What's your best alternative? Other offers, current job, other opportunities.
This determines how aggressive you can be.]

### Recommended Counter-Offer
[Specific numbers for each component, justified by market data.]

| Component | Current Offer | Counter Ask | Justification |
|-----------|--------------|-------------|---------------|
| Base | $[X] | $[Y] | [Market data point] |
| Equity | [X] RSUs | [Y] RSUs | [Market data point] |
| Signing | $[X] | $[Y] | [Rationale] |

### Counter-Offer Script
[Word-for-word email template personalised to this company and situation.
Based on the templates from the base guide, adapted to the specific numbers.]

### Fallback Positions
[If they reject the counter on base, shift to equity. If equity is capped,
shift to signing bonus. The package approach.]

### If They Say "Final Offer"
[The closing move script from the base guide, personalised to this situation.]

## Equity Analysis (if applicable)
[RSU valuation, vesting schedule, tax implications. For AU: Division 83A treatment,
when CGT discount applies, estimated tax bill at vesting.]

## Australian Tax Implications (if AU)
[Effective tax rate on each component. Super structure ("plus super" vs "package").
Salary sacrifice optimisation opportunities. RSU tax planning.]

## Timeline Management
[When to respond. How to coordinate with competing offers. Extension request script.]

## Red Lines
[What would make this offer unacceptable. Where to walk away.]

## Sources
[Links to every data source used — Levels.fyi, Hays, salary-seeker results, Glassdoor, etc.]
```

## Rules

1. **ALWAYS conduct live market research.** Never generate numbers from training data alone. Search Levels.fyi, Glassdoor, Hays, salary-seeker, and company-specific negotiation intelligence.
2. **Source every data point.** When you cite a salary range, link to where you found it.
3. **Personalise the scripts.** The base guide has templates — adapt them with specific numbers, company name, and situation context.
4. **AU-specific analysis when applicable.** Check super structure, RSU taxation, effective tax rates, salary sacrifice opportunities. These materially change the real value of each component.
5. **salary-seeker for AU roles.** If the user has a SEEK job ID, run salary-seeker to extract the hidden range. If they don't have one, search SEEK for the role and extract an ID.
6. **Company-specific patterns.** Use the base guide's company section + live research. Meta lowballs. Amazon back-loads. Apple is tight on base. Netflix is all-cash. Each requires different strategy.
7. **Always recommend counter-offering.** The data shows 66% success rate with 18.83% average increase. The only exception is if the offer is already at P75+ for the company and level.
8. **Include fallback positions.** The negotiation rarely succeeds on the first ask. Build a cascade: base → equity → signing → non-monetary.
9. **Output as a secret GitHub gist.** Write to temp, `gh gist create`, return URL. Requires `gh` CLI.
10. **Note uncertainty.** If data is sparse for this company/role/location, say so. Don't fabricate confidence.
