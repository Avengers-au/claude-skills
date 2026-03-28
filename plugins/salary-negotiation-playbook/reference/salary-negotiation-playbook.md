# Salary & Compensation Negotiation Playbook: Evidence-Based Guide for Tech (2025-2026)

## Overview

This document is a comprehensive, evidence-backed playbook for negotiating salary and total compensation in tech. It covers how tech compensation actually works (base, equity, signing, vesting), market research methodology (Levels.fyi, Blind, salary-seeker for SEEK.com.au), the psychology of negotiation with quantitative evidence, company-specific patterns (Amazon, Meta, Google, Apple, Microsoft, Netflix, startups), word-for-word scripts for every negotiation scenario, equity valuation, and Australian-specific mechanics (superannuation, ESS tax, contractor conversion). The average successful negotiation yields an **18.83% increase** over the initial offer, and **66% of attempts succeed** — yet only 55% of candidates even try.

**What IS covered:** Comp structure anatomy, market research tools (including salary-seeker for AU), negotiation psychology with data, timing and strategy, scripts for every scenario, company-specific patterns, equity deep-dive, AU-specific tax/super/ESS, counter-offer handling, and post-offer email templates.

**What is NOT covered:** Interview preparation (see the interview pipeline playbooks), resume optimisation (see `resume-linkedin-optimiser-guide.md`), or general career strategy.

**Research date:** March 2026. Compensation data and tax rates should be verified at time of use.

---

## Part 1: How Tech Compensation Works

### The Anatomy of a Tech Offer

| Component | What It Is | Typical Range | Negotiability |
|-----------|-----------|---------------|---------------|
| **Base salary** | Stable cash floor | $140K-$300K+ (US), A$80K-$240K+ (AU) | Low-Medium (band-constrained) |
| **Equity (RSUs)** | Restricted Stock Units vesting over 4 years | 25-50% of TC at senior levels | Medium-High (primary lever) |
| **Signing bonus** | One-time payment (clawback if you leave <12 months) | $10K-$100K+ | High (easiest to approve) |
| **Annual bonus** | 15-25% of base, performance-dependent | Varies by company | Low (formulaic) |
| **Refresher grants** | Annual RSU top-ups tied to performance | Meta: up to $400K at E7 | Low (post-hire) |
| **Benefits** | Health, super, relocation, etc. | — | Low |

### The Level Is the Biggest Lever

A single level difference can mean **$50K-$150K+ in annual TC**. Getting levelled correctly matters far more than negotiating within a band. Band width is typically 20% either side of midpoint. The initial offer usually sits at the **25th-50th percentile** of the band — there is typically **15-25% room** above it.

### Vesting Schedules by Company

| Company | Year 1 | Year 2 | Year 3 | Year 4 | Notes |
|---------|--------|--------|--------|--------|-------|
| **Standard** (Google, Meta, Apple, Microsoft) | 25% | 25% | 25% | 25% | 1-year cliff typical |
| **Amazon** | 5% | 15% | 40% | 40% | Heavy signing bonus offsets Years 1-2 |
| **Google** (actual) | 33% | 33% | 22% | 12% | Front-loaded |
| **Meta** | Quarterly, no cliff | — | — | — | Best refreshers in industry |
| **Netflix** | N/A | — | — | — | All-cash, optional 10-year vested options |

### The Trimodal Nature of Tech Comp (Pragmatic Engineer)

| Tier | Who | Comp Range | Characteristics |
|------|-----|-----------|-----------------|
| **Tier 1** | Local companies | ~$65K for senior (non-US) | Benchmark to government sites |
| **Tier 2** | VC-funded startups | 1.5-2x Tier 1 | Compete regionally |
| **Tier 3** | Big Tech, hedge funds | 2-4x Tier 1 | Compete globally, significant equity |

---

## Part 2: Market Research Methodology

### Data Source Reliability

| Source | Best For | Reliability | AU Coverage |
|--------|----------|-------------|-------------|
| **Levels.fyi** | FAANG TC by level | High (W2-verified) | Limited (big tech AU offices) |
| **Blind** | Real-time TC discussions | High for tech (9M+ users) | Very limited |
| **H1B Data** (h1bdata.info) | US base salary (government data) | Very high | N/A (US only) |
| **salary-seeker** | SEEK.com.au hidden salary ranges | High (reveals employer-set data) | Excellent |
| **Hays Salary Guide** | AU salary by role/region | High (12K+ respondents) | Excellent (25 industries, 11 regions) |
| **Robert Half** | AU tech salaries (3 percentiles) | High | Good |
| **Glassdoor** | Directional estimates | Low-moderate (+/-10-25%) | Limited AU |
| **SEEK Salary Guide** | AU advertised ranges | Medium | Broad |

### salary-seeker — Extracting Hidden SEEK Salary Ranges

**What it does:** Bash script that brute-forces the hidden salary range from SEEK.com.au job listings via binary search on URL parameters.

**How to use:**
```bash
# Clone the repo
git clone https://github.com/b3n-j4m1n/salary-seeker.git

# Run with a SEEK job ID (from the URL: seek.com.au/job/38035537)
./salary-seeker.sh 38035537
```

**Browser extension:** `cheesestringer/salary-seeker` provides a Chrome/Firefox extension that shows hidden ranges directly on SEEK listings.

**How it works:** Modifies salary filter parameters in the SEEK URL and uses binary search to find where the job appears/disappears from search results — revealing the advertiser's hidden min/max range.

**Limitations:** Only works when the advertiser has set a range. Returns approximate ranges. May break if SEEK changes URL parameter structure.

### Australian Market Benchmarks (2025)

| Level | Sydney | Melbourne | Brisbane/Remote |
|-------|--------|-----------|-----------------|
| Junior (0-2 yrs) | A$80-100K | A$72-88K | A$65-80K |
| Mid (3-5 yrs) | A$110-140K | A$95-125K | A$85-115K |
| Senior (6-9 yrs) | A$150-190K | A$130-170K | A$120-155K |
| Principal/Staff | A$190-240K | A$175-220K | A$160-200K |

**AI/ML/Cybersecurity premium:** 20-30% above general SWE.

---

## Part 3: The Psychology of Negotiation

### Evidence-Based Negotiation Data

| Finding | Evidence | Implication |
|---------|----------|------------|
| Average increase for those who negotiate | **18.83%** above initial offer | Negotiation is almost always worth it |
| Success rate | **66%** get what they ask for | More than half the time, you get it |
| % who even try | Only **55%** | Most candidates leave money on the table |
| Anchoring effect | Correlation of **.497** between first number and outcome | Never name a number first |
| Power of silence | 3-9 second silences lead to "a-ha" moments (MIT) | Use strategic pauses |
| Competing offers | Single most powerful lever | Interviewing.io: "80% of the work" |

### Who Should Name a Number First?

**Practitioner consensus: NEVER name first.** The company knows their range; you don't.

**Deflection scripts (proven, word-for-word):**

| Situation | Script |
|-----------|--------|
| Early recruiter screen | "I'd like to find out more about the opportunity first. If you make me an offer, I'd be happy to iterate on it." |
| Pushed harder | "I really have no numbers in my head — it depends on the fit and the composition of the offer." |
| Forced to give something | "Can you tell me the salary band for this level? Happy to let you know if it's in my range." |
| Absolute last resort | "The average [role] in [location] makes roughly $X. So I think that's a good place to start." (Anchor to market, not personal floor) |

### Key Psychology Principles

- **BATNA (Best Alternative to a Negotiated Agreement):** Having a competing offer is the most powerful lever. One documented case: a senior Google engineer increased an external offer by ~$600K in 4-year value through 4 negotiation rounds
- **Reciprocity:** When companies concede on one component, signal increased commitment. Pair every ask with enthusiasm
- **The "Yes-If" Principle:** Only negotiate after they've confirmed they want to hire you. Never negotiate from "No-But"
- **Exploding Offers:** Companies give 24-72hr deadlines to prevent comparison shopping. Always request an extension professionally

---

## Part 4: The Negotiation Playbook — Scripts

### The Counter-Offer (Email Recommended)

**For moderate leverage:**
> "The offer you extended was strong. My decision is basically between you and [Company X]. It's a genuinely difficult decision, but there are a couple of dimensions where, if this offer improved, it would be much more compelling."

**For strong leverage (the "Reverse Used Car Salesman"):**
> "I have the following offers, and I'm still interviewing at [Company Y], but I'm really excited about this opportunity and will drop my other processes and SIGN TODAY if [1.5-2x equity, 10-15% base increase, signing bonus of 20%+ base]."

### When Base Is Capped

> "I understand the base is at the top of the band. Could we look at increasing the equity component? I'm confident in [Company]'s trajectory."

### When Everything Is Capped

> "Since base and equity are at their limits, would a signing bonus be possible? Signing bonuses come from a separate budget and don't create ongoing cost."

### "This Is Our Final Offer"

Usually not final. The closing move:
> "I've been thinking it over and it's genuinely a tough decision. I loved everyone at [Company] but the one thing that makes it hard is [specific dimension]. If you can improve [X] by [Y], I'll be totally ready to sign."

### Without Competing Offers

> "I'm also evaluating [staying at current company / grad school / starting my own thing]. I'm excited about [Your Company] and would love to join, but the package has to make sense if I'm going to forego that opportunity."

### Handling Lowball Offers (Meta Is Known for This)

> "I appreciate the offer. I've done extensive research on market rates for this level, and the total compensation is significantly below what I'm seeing at comparable companies. Can we discuss bringing this in line with the market?"

---

## Part 5: Company-Specific Negotiation Patterns

### Amazon

- **Vesting:** 5/15/40/40 back-loaded. Heavy signing bonus in Years 1-2 to offset
- **Base cap:** Doubled from $160K to $350K in 2022 but still capped
- **Primary lever:** Signing bonus — most flexible component. One documented case: $54K signing bonus negotiated
- **Tactic:** "If base can't move, ask for a sizable sign-on bonus to bridge the gap"

### Meta

- **Known for aggressive lowball initial offers** ($50K+ below market)
- **Competing offers create $50K-$150K jumps** in Year 1 TC
- **Quarterly vesting, no cliff.** Best refresher grants in industry
- **Tactic:** Build competing offers before engaging their compensation committee

### Google

- **HC sets the level.** Level is rigid; comp within the band is flexible
- **Down-levelling is common** — fight for correct level before negotiating comp
- **Equity (GSUs) is the primary lever.** In best negotiations, GSUs match base salary
- **Tactic:** If borderline between levels, request to re-interview for the higher level

### Apple

- **Notoriously tight on base** — tightly controlled bands
- **More flexible on equity:** RSU grants negotiable 20-40% above initial with competing offers
- **Signing bonuses flexible** even when not in initial offer ($20K-$50K available)
- **Tactic:** Push on base (knowing they won't move) so they counter on equity/signing

### Netflix

- **All cash, no mandatory equity.** Highest base in FAANG
- **Employees choose annually:** ratio of salary vs 10-year fully vested stock options
- **No golden handcuffs:** "Personal top of market" philosophy

### Startups

- **Equity is in stock options** (ISOs/NSOs), not RSUs
- **Critical questions:** 409A valuation? Strike price? Shares outstanding (fully diluted)? Liquidation preferences?
- **"X% of the company" is misleading** without understanding dilution
- **Rule:** Junior employees should take more cash; risk-tolerant seniors at well-funded startups can take more equity

---

## Part 6: Australian-Specific Compensation

### Superannuation — The $16K Distinction

**Current rate (FY 2025-26): 12%**

| Description | Base Salary | Super (12%) | Total |
|-------------|-------------|-------------|-------|
| "$150,000 **plus** super" | $150,000 | $18,000 | $168,000 |
| "$150,000 **package including** super" | ~$133,929 | ~$16,071 | $150,000 |

**ALWAYS negotiate for "plus super."** The difference at $150K is **$16,071/year.** Ask: "Can we restructure this as base salary plus super?"

### Contractor vs Permanent Conversion

```
Contractor Daily Rate = (Annual Salary × Uplift) / 230 billable days

Uplift factors:
- Conservative: 1.40x (accounts for no leave, no super, gaps)
- Moderate: 1.55x
- Premium: 1.70x (short-term contracts, specialist skills)
```

| Permanent Salary | Conservative (1.4x) | Moderate (1.55x) | Premium (1.7x) |
|-----------------|---------------------|-------------------|-----------------|
| A$150,000 | A$913/day | A$1,011/day | A$1,109/day |
| A$180,000 | A$1,096/day | A$1,213/day | A$1,330/day |
| A$200,000 | A$1,217/day | A$1,348/day | A$1,478/day |

### RSU Taxation in Australia (Division 83A)

| Event | Tax Treatment |
|-------|--------------|
| **Grant** | No tax |
| **Vesting** | Full market value taxed as ordinary income (up to 47%) |
| **Sale within 30 days** | Sale price (not vesting price) determines taxable amount |
| **Sale after 12+ months** | 50% CGT discount on capital gain above vesting price |

**WARNING:** RSU vesting can push you into a higher bracket. $180K base + $50K in RSUs vesting = $230K total income, with RSU portion taxed at 47%.

### Startup ESS Concessions

For eligible startups (<10 years, <$50M turnover, unlisted): tax deferred until sale, up to 15 years. CGT discount (50%) applies if held 12+ months. This makes startup equity significantly more tax-efficient than at public companies.

### Australian Tax Brackets (FY 2025-26)

| Taxable Income | Rate |
|---------------|------|
| $0-$18,200 | 0% |
| $18,201-$45,000 | 16% |
| $45,001-$135,000 | 30% |
| $135,001-$190,000 | 37% |
| $190,001+ | 45% |
| + Medicare Levy | 2% |

**Above $190K, each additional dollar is taxed at 47%.** At this level, non-cash benefits (super salary sacrifice, novated lease, equity with CGT discount) become more valuable per dollar than additional base.

### Salary Sacrifice Optimisation

- **Super salary sacrifice:** Taxed at 15% in fund vs up to 47% as income. Cap: $30,000/year concessional (including employer contributions)
- **Novated lease:** Pre-tax car expenses. **Electric vehicles are FBT-exempt** (as of 2025)
- **Practical saving:** For $200K earner, $6K super sacrifice saves ~$1,920/year in tax

### Redundancy Entitlements (Fair Work Act)

| Years of Service | Redundancy Pay |
|-----------------|---------------|
| 1-2 years | 4 weeks |
| 2-3 years | 6 weeks |
| 3-4 years | 7 weeks |
| 5-6 years | 10 weeks |
| 9-10 years | 16 weeks |

**Bona fide redundancy** has a tax-free component: $13,100 base + $6,552 per completed year (2025-26).

---

## Part 7: Equity Deep-Dive

### RSU vs Stock Options

| Feature | RSUs | Stock Options (NSOs) | ISOs |
|---------|------|---------------------|------|
| What you get | Actual shares at vesting | Right to buy at strike | Right to buy at strike |
| Tax at vest/exercise | Ordinary income on full value | Ordinary income on spread | No income tax (AMT may apply) |
| Common at | Public companies | Startups | Startups (employees only) |

### Evaluating Startup Equity

- Ask: 409A valuation, strike price, fully diluted shares outstanding, liquidation preferences
- **Apply aggressive discounts (50-80%)** when comparing to public company RSUs. Only 1 in 10 VC-backed startups return capital to investors
- Watch for: participating preferred stock (investors "double dip"), multiple liquidation preference multipliers (2x, 3x)

### The Golden Handcuffs Problem

**47% of employees** cite unvested equity as the primary reason they haven't left. When negotiating at a new company, ask for unvested equity to be matched via signing bonus or accelerated RSU grant.

---

## Part 8: Counter-Offer Handling

### Should You Accept Your Current Employer's Counter?

**~70% of employees who accept counter-offers leave within 12 months.** The underlying reasons for departure (growth, management, culture) are rarely addressed by more money.

**When it IS worth considering:**
- The reason for leaving was purely financial and the counter addresses it
- The company offers a new role/team/responsibilities — not just money
- You genuinely prefer staying and hadn't emotionally checked out

---

## Part 9: Post-Offer Email Templates

### Counter-Offer Email

```
Subject: [Your Name] — Thoughts on [Company]'s Offer

Hi [Recruiter],

Thank you for the offer — I'm very enthusiastic about joining [Company].

Before I accept, I'd like to discuss the compensation. Based on my research
and considering [specific value you bring], I believe [specific ask] would
better reflect both market rate and the value I'd contribute.

I'm flexible on how we get there — base, signing bonus, equity, or other
components. I want to find something that works for both of us.

Looking forward to discussing.
[Your Name]
```

### "This Is Final" Response

```
Hi [Recruiter],

I appreciate you working on this. If we could close the remaining gap via
[signing bonus / additional RSUs / extra PTO], I'm ready to accept and
start on [date].

[Your Name]
```

### Declining Gracefully

```
Hi [Recruiter],

Thank you for the [Role] offer. This was genuinely difficult — I was
impressed by the team. After careful consideration, I've decided to
pursue another opportunity that more closely aligns with [reason].

I'd love to stay in touch and happy to refer great people your way.

[Your Name]
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Recruiter insists on a number early | Use deflection scripts from Part 3. Never anchor yourself low |
| Offer is 20%+ below market | Share Levels.fyi/Hays data. Ask: "Can we discuss bringing this in line with market?" |
| "This is our final offer" | Usually not final. Shift to other components (signing bonus, equity) |
| No competing offers | Leverage alternatives: staying at current job, grad school, starting something |
| AU offer says "package including super" | Ask to restructure as "base plus super" — $16K+ difference at $150K |
| RSU vesting will push you into higher tax bracket | Plan for the tax bill. Consider holding shares 12+ months for CGT discount |
| Exploding offer deadline | Request extension: "I want to give this the consideration it deserves. Could we extend to [date]?" |

---

## Sources

- [Haseeb Qureshi — Ten Rules for Negotiating a Job Offer](https://haseebq.com/my-ten-rules-for-negotiating-a-job-offer/) — Core framework: 10 rules, BATNA, external decision-makers, positivity
- [Haseeb Qureshi — How Not to Bomb Your Offer Negotiation](https://haseebq.com/how-not-to-bomb-your-offer-negotiation/) — Rules 7-10, scripts, the "final day" closing move
- [Patrick McKenzie — Salary Negotiation: Make More Money](https://www.kalzumeus.com/2012/01/23/salary-negotiation/) — Never name first, "mouse droppings" framing, compounding effect
- [interviewing.io — What to Say When Recruiters Ask for a Number](https://interviewing.io/blog/negotiate-salary-recruiter) — Deflection scripts, "Reverse Used Car Salesman" counter formula
- [interviewing.io — How to Negotiate with Meta](https://interviewing.io/blog/how-to-negotiate-with-meta) — Meta lowball tactics, $50K-$150K improvements with competing offers
- [Niya Dragova/Lenny's Newsletter — 10 Commandments of Salary Negotiation](https://www.lennysnewsletter.com/p/negotiating-comp) — Phone > email for large increases, myth debunking
- [HBR — 15 Rules for Negotiating a Job Offer (Deepak Malhotra)](https://hbr.org/2014/04/15-rules-for-negotiating-a-job-offer) — Academic framework, bundling, synchronising offers
- [The Interview Guys — Every Salary Negotiation Study 2024-2025](https://blog.theinterviewguys.com/we-reviewed-every-salary-negotiation-study/) — 18.83% average increase, 66% success rate, anchoring data
- [Harvard PON — Anchoring in Negotiation](https://www.pon.harvard.edu/daily/negotiation-skills-daily/what-is-anchoring-in-negotiation/) — .497 correlation, $100K anchor experiment
- [MIT Sloan — Use Silence to Improve Outcomes](https://mitsloan.mit.edu/ideas-made-to-matter/negotiation-use-silence-to-improve-outcomes-all) — 3-9 second silence research
- [Pragmatic Engineer — Trimodal Nature of Tech Compensation](https://newsletter.pragmaticengineer.com/p/trimodal-nature-of-tech-compensation) — Three-tier model
- [Fearless Salary Negotiation — Big Tech Offer Overview](https://fearlesssalarynegotiation.com/big-tech-job-offer-overview/) — Anatomy of tech offers
- [Fearless Salary Negotiation — Counter-Offer Email Templates (Josh Doody)](https://fearlesssalarynegotiation.com/salary-negotiation-email-sample/) — 10-20% counter rule
- [Candor — Salary Negotiation Strategies](https://candor.co/guides/salary-negotiation) — Comp band mechanics, equity leverage
- [salary-seeker (b3n-j4m1n/salary-seeker)](https://github.com/b3n-j4m1n/salary-seeker) — Bash script extracting hidden SEEK.com.au salary ranges
- [salary-seeker Chrome Extension (cheesestringer)](https://github.com/cheesestringer/salary-seeker) — Browser extension for SEEK salary ranges
- [Hays Salary Guide FY25/26](https://www.hays.com.au/salary-guide) — 12K+ respondents, 1K+ roles, 25 industries, 11 AU regions
- [Robert Half AU Technology Salary Guide](https://www.roberthalf.com/au/en/insights/salary-guide/technology) — Three-percentile data
- [Levels.fyi 2025 Pay Report](https://www.levels.fyi/2025/) — Verified comp benchmarks
- [ATO — Employee Share Schemes](https://www.ato.gov.au/businesses-and-organisations/corporate-tax-measures-and-assurance/employee-share-schemes) — Division 83A rules, ESS taxation
- [ATO — Key ESS Changes](https://www.ato.gov.au/businesses-and-organisations/corporate-tax-measures-and-assurance/employee-share-schemes/in-detail/key-ess-changes-in-detail) — 15-year deferral, startup concessions
- [Baker McKenzie — RS/RSU Australia](https://resourcehub.bakermckenzie.com/en/resources/global-equity-matrix/asia-pacific/australia/topics/rsrsu) — RSU taxation at vesting, CGT discount
- [SuperGuide — SG Rate](https://www.superguide.com.au/super-booster/superannuation-guarantee-sg-contributions-rate) — 12% from 1 July 2025
- [Fair Work — Redundancy Pay](https://www.fairwork.gov.au/ending-employment/redundancy/redundancy-pay) — NES redundancy scale
- [CNBC — $54K Amazon Signing Bonus](https://www.cnbc.com/2025/03/19/i-negotiated-a-54000-sign-on-bonus-at-amazon-heres-my-best-advice-negotiating-salary.html) — Real Amazon negotiation case study
- [KFA Private Wealth — Amazon RSU Vesting](https://kfapwg.com/2025/03/navigating-amazons-unique-rsu-vesting-schedule-a-strategic-guide-for-employees/) — Amazon 5/15/40/40 structure
- [Ravio — Netflix Compensation Strategy](https://ravio.com/blog/compensation-strategy-examples-netflix) — All-cash philosophy
- [The Finance Buff — Golden Handcuffs](https://thefinancebuff.com/unvested-rsus-as-golden-handcuffs-what-to-do.html) — 47% retention factor
