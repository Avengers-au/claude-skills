---
name: validate
description: >-
  Use this skill when the user wants to validate a startup or business idea
  before building it. Trigger on "validate this idea", "market gap analysis",
  "run the checklist", "is this idea worth building", "validate market gap",
  "kill or proceed", "gate check this idea", "should we build this",
  "market validation", "idea validation", "competitive landscape check",
  "does this problem exist", or any request to systematically evaluate whether
  a business idea has a real market gap worth pursuing.
user-invocable: true
allowed-tools: Bash(gh *), Read, WebSearch, WebFetch
argument-hint: <idea-description> [target-market]
---

# Market Gap Validation

Validate a startup or business idea against a rigorous 6-gate checklist using live web research. The skill walks through each gate sequentially, conducting real searches at every step, and produces a structured validation report with PASS/FAIL/PARTIAL verdicts. The core discipline: **kill bad ideas fast**.

No one-pager gets written until every gate is completed. If a gate fails, the idea is killed and documented.

## Required Inputs

- **Idea description** (required): What is the problem and proposed solution? Be specific — "farm compliance software" not "helping farmers"
- **Target market** (optional, default: Australia): The country or region to validate against

## Step 1: Read the Reference Checklist

Read the bundled reference checklist for the complete gate criteria. Locate it locally first, then fall back to the GitHub API:

```bash
find ~/.claude -name "market-gap-validation-checklist.md" -path "*/market-gap-validation/*" 2>/dev/null | head -1
```

If not found locally, fetch from the source repo:

```bash
gh api repos/Avengers-au/claude-skills/contents/plugins/market-gap-validation/reference/market-gap-validation-checklist.md --jq '.content' | base64 -d
```

Read the reference doc to internalise the exact checklist items, red flags, and process. Every gate below maps to the reference.

## Step 2: Gate 1 — Does the Problem Actually Exist?

**Goal:** Find hard evidence that this problem is real, quantified, and getting worse.

### Research Actions (ALL mandatory)

1. **Authoritative sources (3+ required):**
   - `WebSearch` for `"[problem] government report [country]"`
   - `WebSearch` for `"[problem] industry report [country]"`
   - `WebSearch` for `"[problem] research study [country]"`
   - `WebSearch` for `"[problem] [industry body] report"`
   - Acceptable sources: government departments, industry peak bodies, peer-reviewed research, ABS/census data, Royal Commission transcripts. NOT blog posts, vendor marketing, or opinion pieces.

2. **Quantified dollar impact:**
   - `WebSearch` for `"[problem] cost to business [country]"`
   - `WebSearch` for `"[problem] economic impact [country]"`
   - Look for: cost per business, industry-wide cost, lost revenue figures, fine amounts, hours wasted. Actual numbers with citations.

3. **Real complaints:**
   - `WebSearch` for `"[problem] reddit [industry]"`
   - `WebSearch` for `"[problem] forum complaint"`
   - `WebSearch` for `"[problem] [industry] facebook group"`
   - Check relevant subreddits if Reddit MCP tools are available (e.g., `mcp__reddit__get_subreddit_hot_posts` for industry-specific subreddits)
   - Look for: forum posts, survey results, conference talks, interview transcripts where real people describe this pain

4. **Getting worse (tailwind check):**
   - `WebSearch` for `"[problem] [industry] trends [current year]"`
   - `WebSearch` for `"[problem] new regulation [country]"`
   - Is there new regulation, growing demand, rising costs, or increasing complexity? A tailwind, not a static situation.

5. **Forcing function:**
   - `WebSearch` for `"[industry] regulatory deadline [country] [current year]"`
   - `WebSearch` for `"[industry] program change [country]"`
   - Is there a specific deadline, program change, or industry shift making this urgent NOW?

### Verdict

Rate each checklist item:
- ✅ **Met** — evidence found with source
- ⚠️ **Partial** — some evidence but gaps
- ❌ **Not met** — no evidence found

**Gate 1 overall:** PASS (4-5 items met) / PARTIAL (2-3 items met) / FAIL (0-1 items met)

**If FAIL:** Stop immediately. Generate abbreviated report (skip Gates 2-6). The problem may not exist or may not be severe enough to build a business around.

---

## Step 3: Gate 2 — Who Exactly Is the Buyer?

**Goal:** Identify a specific, reachable, countable buyer who will pay.

### Research Actions (ALL mandatory)

1. **Specific job title:**
   - From Gate 1 research, identify who actually experiences this pain daily
   - NOT "farmers" — which farmers? The owner-operator? The farm manager? The agronomist? The contractor?
   - NOT "healthcare providers" — the GP? The practice manager? The nurse unit manager?
   - Name ONE specific job title

2. **Buyer count in target market:**
   - `WebSearch` for `"how many [job title] in [country]"`
   - `WebSearch` for `"[job title] [country] industry statistics"`
   - `WebSearch` for `"[industry] businesses [country] ABS"` (or equivalent statistical body)
   - Need an exact number with a source — not "thousands" or "lots"

3. **Current spending:**
   - `WebSearch` for `"[job title] [problem] software spending"`
   - `WebSearch` for `"[industry] technology adoption [country]"`
   - What do they currently pay to solve this? Even if $0 on software — what's the cost in time, consultant fees, fines, or errors?

4. **Distribution channel:**
   - `WebSearch` for `"[industry] association [country]"`
   - `WebSearch` for `"[industry] conference [country] [current year]"`
   - `WebSearch` for `"[industry] [country] facebook group"`
   - Identify ONE specific channel: an industry association, a conference, a Facebook group, a dealer network, a professional network. NOT "digital marketing" or "SEO".

5. **Willingness to pay:**
   - `WebSearch` for `"[industry] software pricing [country]"`
   - `WebSearch` for `"[adjacent tool] pricing"`
   - Find pricing of adjacent tools this buyer already pays for. If they pay $50/month for accounting software, a $49/month compliance tool is plausible. If they pay $0 for everything, that is a signal.

### Verdict

Rate each checklist item: ✅ Met / ⚠️ Partial / ❌ Not met

**Gate 2 overall:** PASS / PARTIAL / FAIL

**If FAIL:** Stop immediately. Generate abbreviated report (skip Gates 3-6). No identifiable buyer means no business.

---

## Step 4: Gate 3 — What Do They Use Today?

**This is the gate we skipped. Never again.**

Gate 3 is the most research-intensive gate. Execute ALL of the following searches — do not skip any.

### Research Actions (ALL mandatory — no exceptions)

1. **Problem + app search:**
   - `WebSearch` for `"[problem] app [country]"`
   - Document every result

2. **Problem + software search:**
   - `WebSearch` for `"[problem] software [country]"`
   - Document every result

3. **App store search:**
   - `WebSearch` for `"[problem] app" site:apps.apple.com OR site:play.google.com`
   - `WebSearch` for `"[relevant keywords] app store reviews"`
   - Note: download counts, star ratings, review themes

4. **Software review platforms:**
   - `WebSearch` for `"[problem] software [country]" site:capterra.com`
   - `WebSearch` for `"[problem] software [country]" site:getapp.com`
   - `WebSearch` for `"[problem] software" site:g2.com`
   - `WebSearch` for `"[problem] software" site:softwareadvice.com`
   - Note: number of reviews, ratings, pricing listed

5. **Industry management software:**
   - `WebSearch` for `"[industry] management software [country] competitors"`

6. **Alternatives search (surfaces the full landscape):**
   - From results so far, identify the biggest player
   - `WebSearch` for `"[biggest player] alternatives"`
   - `WebSearch` for `"[biggest player] competitors"`
   - This single query often surfaces the entire competitive landscape

7. **Startup search:**
   - `WebSearch` for `"[problem] startup [country]" site:producthunt.com`
   - `WebSearch` for `"[problem] [industry]" site:crunchbase.com`
   - `WebSearch` for `"[problem] [industry] startup" site:linkedin.com`

### Build the Competitor Table

For EVERY competitor found, document:

| Name | Country | Founded | Pricing | Key Features | Funding | Est. Users/Revenue |
|------|---------|---------|---------|-------------|---------|-------------------|
| [name] | [country] | [year] | [pricing] | [features] | [amount] | [estimate] |

Use `WebFetch` on competitor websites to get accurate pricing and feature lists.

### The Critical Question

For each competitor, answer: **Does it do the SPECIFIC thing we're proposing?** Not adjacent features — the actual core workflow we identified in Gate 1. Be brutally honest.

### Verdict

**Gate 3 overall:**
- **PASS** — Competitors exist but none address the specific workflow/segment we identified
- **PARTIAL** — Some competitors partially address it; differentiation is narrow
- **FAIL** — Multiple competitors already do exactly what we're proposing

**If FAIL:** Stop. Existing tools already solve this. Generate report explaining what exists.

**⚠️ WARNING:** If NO competitors are found, this is a RED FLAG, not a green light. Either we haven't searched hard enough, or there's a reason nobody is building this. Go back and search harder before declaring the landscape empty.

---

## Step 5: Gate 4 — Where Is the Actual Gap?

**Only proceed if Gate 3 is complete.** This gate synthesises Gates 1-3.

### Analysis (answer each question with evidence)

1. **Underserved segment:** Is there a segment of buyers that existing tools don't serve? (Too small, too regional, wrong industry sub-type, wrong price point)

2. **Broken workflow:** Is there a specific workflow within the problem that no tool handles well? NOT "they all suck" — which EXACT step is broken or missing?

3. **Technology shift:** Is there a technology shift enabling a new approach? (AI, new API, new data source, mobile-first, offline-first — something that didn't exist when incumbents were built)

4. **Recent regulatory change:** Is there a regulatory or program change so recent that incumbents haven't adapted yet?

5. **Pricing gap:** Are existing tools priced out of reach for the target segment? (Enterprise pricing for a small-business problem)

6. **Complexity gap:** Are existing tools too complex for the target user? (Feature bloat when the buyer wants one thing done well)

7. **The One Sentence Test:** Can we articulate the gap in ONE sentence WITHOUT using the words "better", "simpler", or "cheaper"?
   - ✅ Good: "No existing tool generates NVD chemical spray records pre-populated from the APVMA database for broadacre grain growers"
   - ❌ Bad: "We'll be simpler and cheaper than FarmLogs"
   - If you cannot pass this test, the gap probably isn't real.

### Verdict

**Gate 4 overall:** PASS (gap clearly articulated with evidence) / PARTIAL (gap exists but narrow) / FAIL (no genuine gap identified)

---

## Step 6: Gate 5 — Can We Actually Build It?

### Assessment

1. **MVP timeline:** Can two engineers ship an MVP in 10-12 weeks? If not, scope is too big — what can be cut?

2. **Data sources:**
   - `WebSearch` for `"[required data] API"` or `"[required data] public database"`
   - `WebSearch` for `"[government data source] API documentation"`
   - `WebFetch` on any API documentation URLs found
   - Confirm the data sources ACTUALLY EXIST and are USABLE. Don't assume. Check API docs, terms of use, rate limits.

3. **Domain expertise:** Does the solution require domain expertise the team doesn't have? If yes, can we get a domain advisor before building?

4. **Offline requirement:** If the target user is in regional/rural areas, does the solution work offline? This is non-negotiable for many Australian industries.

5. **Standalone v1:** Is there a clear first version that delivers value WITHOUT needing integrations, partnerships, or marketplace effects?

### Verdict

**Gate 5 overall:** PASS / PARTIAL / FAIL

---

## Step 7: Gate 6 — Will It Make Money?

### Revenue Modelling

1. **Price point:**
   - Based on Gate 2 research (what buyer already pays for adjacent tools)
   - `WebSearch` for `"[similar tool] pricing [country]"` if not already researched
   - State the realistic monthly price: $X/month

2. **$1M ARR calculation:**
   - Customers needed = $1,000,000 / ($X × 12)
   - Is that number plausible given the total buyer count from Gate 2?
   - Example: $49/month × 12 = $588/year. Need 1,701 customers for $1M ARR. If there are 5,000 buyers in Australia, that's 34% market share — very ambitious.

3. **Revenue type:** One-time sale or recurring subscription? Recurring = sustainable. One-time = need volume and repeat purchases.

4. **Buyer = user alignment:** Is the person using it daily the same person who pays? If not (e.g., farm worker uses it, farm owner pays), the sales cycle is harder and adoption is slower.

5. **Expansion path:** Where does growth come from after v1?
   - Adjacent workflows (compliance → record-keeping → reporting)?
   - Adjacent segments (grain → livestock → horticulture)?
   - Adjacent markets (Australia → New Zealand → similar regulatory environments)?

### Verdict

**Gate 6 overall:** PASS / PARTIAL / FAIL

---

## Step 8: Red Flags Scan

Check the idea against EVERY red flag below. Be honest.

| Red Flag | Assessment |
|----------|-----------|
| "There are lots of competitors but they all suck" — if 8 companies can't solve it, maybe the problem isn't solvable with software | [Does this apply? Y/N + reasoning] |
| "Farmers/providers/operators just need to be educated" — if adoption is the problem, more software won't fix it | [Does this apply? Y/N + reasoning] |
| "We'll be simpler" — every competitor's landing page already says "simple" and "easy to use" | [Does this apply? Y/N + reasoning] |
| "The market is huge" — huge markets attract huge competitors with huge budgets | [Does this apply? Y/N + reasoning] |
| "Nobody is doing this" — either we haven't looked hard enough, or there's a reason nobody is doing it | [Does this apply? Y/N + reasoning] |
| We can't find a single person online complaining about this specific problem — the problem might not be real enough to pay for | [Does this apply? Y/N + reasoning] |

If ANY red flag triggers, note it prominently in the recommendation.

---

## Step 9: Generate the Report

Write the validation report to a temporary file:

```bash
IDEA_SLUG=$(echo "[idea-name]" | tr '[:upper:]' '[:lower:]' | tr ' ' '-' | tr -cd '[:alnum:]-')
REPORT_FILE="$TMPDIR/market-gap-validation-${IDEA_SLUG}.md"
```

The report MUST follow this structure:

```markdown
# Market Gap Validation Report: [Idea Name]

**Date:** [YYYY-MM-DD]
**Target Market:** [country]
**Overall Verdict:** PROCEED / KILL / PROCEED WITH CAUTION

## Summary
[2-3 sentence executive summary. State the verdict and the single most important finding.]

## Gate Results

| Gate | Verdict | Key Finding |
|------|---------|-------------|
| 1. Problem Exists? | PASS/FAIL/PARTIAL | [one-liner] |
| 2. Buyer Identified? | PASS/FAIL/PARTIAL | [one-liner] |
| 3. Competitive Landscape | PASS/FAIL/PARTIAL | [one-liner] |
| 4. Gap Identified? | PASS/FAIL/PARTIAL | [one-liner] |
| 5. Buildable? | PASS/FAIL/PARTIAL | [one-liner] |
| 6. Revenue Model? | PASS/FAIL/PARTIAL | [one-liner] |

## Gate 1: Problem Existence
### Checklist
[Each item with ✅/⚠️/❌ and evidence]
### Sources Found
[Numbered list of authoritative sources with URLs]
### Verdict: [PASS/FAIL/PARTIAL]
[1-2 sentence justification]

## Gate 2: Buyer Identification
### Buyer Profile
- **Job title:** [specific title]
- **Count in [country]:** [number] ([source])
- **Current spend:** [amount or description]
- **Channel:** [specific channel]
- **Price sensitivity:** [based on adjacent tool pricing]
### Verdict: [PASS/FAIL/PARTIAL]
[1-2 sentence justification]

## Gate 3: Competitive Landscape
### Competitor Table
| Name | Country | Founded | Pricing | Key Features | Funding | Does It Do Our Thing? |
|------|---------|---------|---------|-------------|---------|----------------------|
[Every competitor found]
### Analysis
[Which competitors come closest? What do they miss?]
### Verdict: [PASS/FAIL/PARTIAL]

## Gate 4: Gap Identification
### The Gap Statement
> [One sentence articulating the gap WITHOUT "better", "simpler", or "cheaper"]
### Evidence
[Supporting analysis for each gap dimension]
### Verdict: [PASS/FAIL/PARTIAL]

## Gate 5: Buildability Assessment
### Technical Feasibility
[Data sources, APIs, offline requirements, domain expertise]
### MVP Scope
[What's in v1, what's deferred]
### Verdict: [PASS/FAIL/PARTIAL]

## Gate 6: Revenue Model
### Unit Economics
- **Price point:** $[X]/month
- **Customers for $1M ARR:** [number]
- **Total addressable buyers:** [number from Gate 2]
- **Required market share:** [percentage]
- **Revenue type:** Recurring / One-time
- **Buyer = User:** Yes / No
### Expansion Path
[Workflows → Segments → Markets]
### Verdict: [PASS/FAIL/PARTIAL]

## Red Flags Check
[Table of all 6 red flags with Y/N assessment]

## Recommendation
**[PROCEED / KILL / PROCEED WITH CAUTION]**

[2-3 paragraphs with specific reasoning. If KILL: explain exactly which gate(s) failed and why. If PROCEED WITH CAUTION: explain the risks and what needs to be resolved before committing. If PROCEED: explain the strongest evidence and what to do next.]

## Next Steps
[If PROCEED: what to do next (write the one-pager, talk to N potential buyers, etc.)]
[If KILL: what to investigate instead, or what adjacent idea might work]

## Sources
[Every URL referenced in the report, with 1-line annotation]
- [Source Title](URL) — [what was extracted from this source]
```

## Step 10: Publish as Gist

Create a secret GitHub gist so the report is shareable:

```bash
gh gist create "$REPORT_FILE" -d "Market Gap Validation: [Idea Name]"
```

Copy the URL to clipboard on macOS:

```bash
echo "$GIST_URL" | pbcopy 2>/dev/null
```

Return the gist URL to the user. The report is now accessible from any device.

---

## Error Handling

| Error | Response |
|-------|----------|
| `gh` not installed | Tell user to install from https://cli.github.com |
| `gh` not authenticated | Tell user to run `gh auth login` |
| No authoritative sources found for Gate 1 | Flag as FAIL — if the problem can't be sourced with 3+ authorities, it may not exist at scale |
| Competitor search returns zero results | **WARNING:** This is a red flag, not a green light. "Nobody is doing this" means either insufficient searching or a reason it hasn't been built. Search harder before declaring empty. |
| Target market too niche for public data | Note data limitations explicitly. Recommend primary research (interviews, surveys) to fill gaps. Mark affected items as ⚠️ Partial. |
| WebSearch returns irrelevant results | Rephrase the query. Try alternative terms, industry jargon, or regional terminology. Document what was searched and what wasn't found. |
| Gist creation fails | Save the report locally and provide the file path instead. The report content is the value — the gist is a convenience. |

---

## Rules

1. **Actually search** — every gate requires live `WebSearch` and `WebFetch` research. Do NOT rely on training data. The value of this skill is CURRENT, SPECIFIC information. If a claim doesn't have a source URL, it doesn't count.
2. **Kill fast** — if Gate 1 or Gate 2 FAIL, stop immediately. Skip remaining gates. Generate an abbreviated report explaining why. Do not waste research time on an idea with no proven problem or no identifiable buyer.
3. **Be honest, not optimistic** — the value is in killing bad ideas, not validating them. Confirmation bias is the enemy. If evidence is weak, say so. If a gate barely passes, flag it.
4. **Cite everything** — every factual claim needs a source URL. "According to [source]" is required, not optional. Unsourced claims are marked as unverified.
5. **No weasel words** — verdicts are PASS, FAIL, or PARTIAL. Not "promising", "interesting", "could work", or "worth exploring". Binary discipline.
6. **Gate 3 is sacred** — this is "the gate we skipped. Never again." Run ALL the searches listed. Do not abbreviate. Do not skip the App Store check. Do not skip the alternatives search. If Gate 3 is incomplete, the entire validation is invalid.
7. **Red flags are automatic** — always run the red flags scan, even if all 6 gates pass. A passing idea with red flags needs caution noted.
8. **One sentence gap test** — Gate 4 MUST produce a gap statement that does not contain the words "better", "simpler", or "cheaper". If it can't, the gap is not real.
9. **Numbers over narratives** — prefer "$47,000 average annual compliance cost (Source: ABARES 2024)" over "compliance is expensive for farmers". Quantify everything.
10. **Output as a gist** — write the report to a temp file and create a secret gist with `gh gist create`. Return the gist URL so the user can share it with co-founders, advisors, or investors. If `gh` is unavailable, save locally and provide the path.
