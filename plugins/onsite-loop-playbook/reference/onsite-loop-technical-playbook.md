# Onsite/Loop Technical Rounds Playbook: The Complete Multi-Round Survival Guide

## Overview

This document is the definitive, evidence-backed playbook for the technical components of onsite/loop interviews at major tech companies. The onsite is the final, most intensive evaluation — typically 4-8 rounds over 4-6 hours comprising system design, coding deep-dives, domain-specific rounds, and architecture reviews. This guide covers company-specific loop structures, system design frameworks, onsite coding strategy, the debrief mechanics candidates never see, energy management across the marathon, question prediction techniques, and post-onsite tactics.

This guide is a **foundation that must be supplemented with live research**. The accompanying skill conducts fresh Glassdoor/company research for every playbook it generates.

**What IS covered:** Company-specific loop structures (Amazon, Meta, Google, Apple, Microsoft, Netflix, Stripe, Anthropic, Palantir, startups), system design framework and the 15 most common questions, onsite coding strategy with pattern frequency data, debrief mechanics, energy management, question prediction, social engineering, post-onsite tactics, and failure recovery.

**What is NOT covered:** Behavioural rounds (see `behavioural-interview-playbook.md`), phone screen coding (see `technical-phone-screen-playbook.md`), or recruiter/HM screens (see respective playbooks).

**Research date:** March 2026. Company processes change quarterly — always supplement with live research.

---

## Part 1: Company-Specific Loop Structures

### Amazon — The Loop

| Aspect | Detail |
|--------|--------|
| **Rounds** | 4-6 interviews (scales with level: L5=5, L7=7), 45-60 min each |
| **Breakdown** | 3 coding + 1 system design + 1 behavioural + hiring manager |
| **Unique features** | LP evaluation in EVERY round (not just behavioural). Bar Raiser with veto. Pre-brief meeting before onsite |
| **Format (2025)** | Mostly virtual. LiveCode editor (syntax highlighting, no execution) |
| **Decision** | Pre-brief → Loop → Written feedback (24-48hr) → Debrief (Day 4-7) → Decision (5-14 business days) |
| **Pass rate** | ~3% of candidates pass the full loop |

**Bar Raiser:** External senior employee from outside the team. Has absolute veto — "If the Bar Raiser says no, you do not get hired, even if every other interviewer says yes." Both Bar Raiser AND hiring manager must agree for a hire.

### Meta — The Onsite

| Aspect | E5 (Senior) | E6 (Staff) |
|--------|------------|------------|
| **Rounds** | 4-5 rounds, 45 min each | 5 rounds + Leadership Assessment pre-screen |
| **Coding** | 2 standard coding rounds | 1 standard + 1 AI-assisted (pilot Q4 2025) |
| **System Design** | 1 round (high-level) | 1 architecture + 1 design (low-level) |
| **Behavioural** | 1 Jedi round | 1 Jedi (higher bar) |
| **Down-levelling** | ~55% of candidates are down-levelled | System design drives levelling |

**AI-assisted coding round (new Oct 2025):** 60 minutes in CoderPad with embedded AI (GPT-4o mini, GPT-5, Claude Sonnet, Gemini, Llama). Multi-file project (hundreds of lines), NOT algorithmic. Three phases: bug fixing → core implementation (120+ lines) → optimisation. **Warning:** Multiple candidates report AI performing significantly worse during actual interviews vs practice — likely system prompt restrictions.

### Google — The Onsite

| Aspect | Detail |
|--------|--------|
| **Rounds** | 4-6 rounds, 45 min each |
| **Breakdown** | 2-3 coding + 1 system design (L4+) + 1 Googleyness & Leadership |
| **Key insight** | Google is the ONLY FAANG where coding > system design in importance |
| **Decision** | Hiring committee of 4-5 senior SWEs who NEVER met you review the packet. Consensus (not majority vote) |
| **Scoring paradox** | "Five scores of 'Leaning Hire' most likely results in No Hire" — committee wants strong signals |

**Google layers complexity:** After solving the initial problem, interviewers add constraints: "What if the input doesn't fit in memory?" Your initial solution must be extensible.

### Apple — The Loop

| Aspect | Detail |
|--------|--------|
| **Rounds** | 6-8 in-person rounds, 45-60 min each |
| **Unique features** | Two interviewers per round (pair interviewing). Lunch IS part of the interview |
| **Standardisation** | None — each team designs its own format |
| **Decision** | Informal same-day thumbs-up/down; hiring manager has most authority |
| **Pass rate** | ~10% |

### Microsoft — The Loop

| Aspect | Detail |
|--------|--------|
| **Rounds** | 4-5 rounds, 1 hour each |
| **AA Round** | Final "As-Appropriate" interview with Principal+ — can override ALL earlier feedback |
| **AA Trigger** | Only occurs if 2+ earlier rounds said "Hire" |
| **Format** | Virtual on Microsoft Teams |

### Netflix

| Aspect | Detail |
|--------|--------|
| **Rounds** | ~8 rounds (split across 2 days recommended) |
| **Key insight** | System design is the MOST important round (opposite of Google) |
| **Unique** | Directors routinely participate. "Dream Team" behavioural round with directors. Culture memo is REQUIRED reading |

### Stripe

| Aspect | Detail |
|--------|--------|
| **Rounds** | 4-6 rounds, 1 hour each |
| **Integration round** | Real GitHub repo, real API docs, full internet access — build working features |
| **Bug bash** | Buggy codebase with failing tests; identify and fix under pressure |
| **Coding style** | NOT LeetCode — practical engineering. Code quality > algorithmic optimality |

### Anthropic

| Aspect | Detail |
|--------|--------|
| **Rounds** | 4 rounds over 4 hours (virtual) |
| **Pre-onsite** | 90-min CodeSignal take-home + 1-hour HM deep dive |
| **Coding style** | Progressive complexity (e.g., build in-memory database from basic to advanced) |
| **Design focus** | AI-specific: LLM inference serving, distributed search, GPU memory optimisation |

---

## Part 2: System Design Framework

### The Delivery Framework (45 Minutes)

| Phase | Time | What To Do |
|-------|------|-----------|
| **1. Requirements** | ~5 min | 3-5 functional requirements + 3-5 non-functional requirements (quantified). State what's OUT of scope |
| **2. Core Entities** | ~2 min | 3-5 fundamental data objects. Keep minimal |
| **3. API / Interface** | ~5 min | REST endpoints or gRPC. Derive user identity from auth, never request bodies |
| **4. High-Level Design** | ~10-15 min | Draw architecture. Build incrementally by walking through each API endpoint |
| **5. Deep Dives** | ~10-15 min | Iterate on baseline to satisfy non-functional requirements. **Senior candidates should lead this; juniors expect interviewer probes** |
| **6. Trade-offs** | ~5 min | Stress-test your own design. What breaks at 10x? What alternatives exist? |

### Level Expectations in System Design

| Dimension | L4 (Mid) | L5 (Senior) | L6 (Staff) | L7 (Principal) |
|-----------|----------|-------------|------------|-----------------|
| **Who drives** | Interviewer 50-60% | Candidate 70-80% | Candidate 90%+ | Candidate 95%+, educates |
| **Requirements** | Identifies obvious functionals with prompting | Identifies functional + non-functional independently | Frames in business context, scopes aggressively | Reframes the problem if needed |
| **Depth** | Solid on 1 component when prompted | Deep on 2+ components proactively | Deep across multiple domains, may introduce novel approaches | Industry-leading, influences how interviewer thinks |
| **Trade-offs** | Discusses when asked | Proactively identifies, discusses 2-3 alternatives | Quantifies, discusses second-order effects | Frames in business/org impact |
| **Operational** | Mentions monitoring when prompted | Discusses alerting, deployment strategy | Proposes SLOs, graceful degradation | Team structure implications, runbook design |

**The critical L5→L6 distinction:** "The difference was rarely about knowing more technologies. It was about how they used what they already knew."

### Back-of-Envelope Numbers to Memorise

| Metric | Value |
|--------|-------|
| Seconds per month | ~2.5 million |
| 1M req/month | 0.4 req/sec |
| 100M req/month | 40 req/sec |
| 1B req/month | 400 req/sec |
| Redis | 100K+ req/sec, sub-ms latency, up to 1 TB |
| Single PostgreSQL | 10-20K TPS, dozens of TB |
| Kafka broker | 1M messages/sec |
| Regional latency | 1-2 ms |
| Cross-region latency | 50-150 ms |

### The 15 Most Common System Design Questions

| Question | What It Really Tests | Key Components | Common Pitfall |
|----------|---------------------|----------------|----------------|
| **URL Shortener** | Hash generation, read-heavy systems | Base62 encoding, KGS, caching, 301 vs 302 | Over-engineering a "simple" question |
| **Twitter/X Feed** | Fan-out, push vs pull, ranking | Fan-out-on-write (normal), fan-out-on-read (celebrities), timeline cache | Not handling celebrity problem |
| **Chat System** | Real-time, presence, ordering | WebSockets, message queue, ordering guarantees, E2E encryption | Ignoring message ordering |
| **Notification System** | Multi-channel delivery, reliability | Queue per channel, retry with backoff, rate limiting, preference service | No deduplication |
| **Rate Limiter** | Distributed systems, consistency | Token bucket or sliding window, Redis, race conditions | Not discussing distributed case |
| **Web Crawler** | Distributed processing, politeness | URL frontier, DNS cache, robots.txt, dedup (SimHash), coordination | URL traps/infinite loops |
| **YouTube/Video Streaming** | Upload pipeline, CDN, adaptive streaming | Chunked upload, transcoding, HLS/DASH, CDN delivery | Ignoring upload-to-playable pipeline |
| **Google Maps** | Geospatial, graph algorithms | Tile rendering, graph partitioning, Dijkstra/A*, real-time traffic | Over-focusing on routing algorithm |
| **Search Engine** | Indexing, ranking, query processing | Crawler, inverted index, TF-IDF/PageRank, query parsing, caching | Over-focusing on ranking vs system |
| **Payment System** | Strong consistency, idempotency | Idempotent API, double-entry ledger, async reconciliation, PCI | Not discussing idempotency |
| **Ad Serving** | Low latency, auction, targeting | RTB pipeline, second-price auction, CTR prediction, budget pacing | Not discussing 100ms latency constraint |
| **Distributed Cache** | Consistency, eviction, partitioning | Consistent hashing, LRU/LFU, write-through/behind, invalidation | Not discussing cache invalidation |
| **Task Scheduler** | Distributed coordination, reliability | Priority queue, worker pool, retry, dead letter queue | Not handling worker failure |
| **File Storage (Dropbox)** | Sync, chunking, conflict resolution | Chunked storage, dedup, version vectors, conflict resolution | Not discussing chunking/dedup |
| **Ride-Sharing (Uber)** | Real-time matching, geospatial, pricing | Matching service, geohash, surge pricing, trip state machine | Not discussing matching constraints |

### System Design for Non-Traditional Roles

| Role Category | Framework | Focus Areas |
|--------------|-----------|-------------|
| **Frontend** | RADIO (Requirements, Architecture, Data Model, Interface, Optimisation) | Component architecture, state management, rendering performance, a11y |
| **ML/AI** | 9-step (Problem → Metrics → Architecture → Data → Features → Model → Serving → Testing → Monitoring) | Feature stores, training-serving skew, model versioning, A/B testing |
| **Mobile** | Backend framework + offline-first, sync, battery, networking constraints | Unreliable networks, OS limits, device diversity |
| **Security** | STRIDE/SALT integrated into architecture | Attack surface per component, trust boundaries, encryption layers |
| **Data** | Pipeline-focused (batch vs real-time, warehousing, quality) | ETL/ELT patterns, schema evolution, data quality gates |
| **Infra/SRE** | Reliability-focused (SLOs, observability, capacity planning) | Graceful degradation, chaos engineering, deployment strategies |

---

## Part 3: Onsite Coding Strategy

### How Onsite Coding Differs from Phone Screen

| Dimension | Phone Screen | Onsite |
|-----------|-------------|--------|
| **Difficulty** | LC Easy-Medium | LC Medium-Hard (the bar rose 15% since 2022) |
| **Problems per round** | 2 problems, 45 min | 1 problem with follow-ups, 45-60 min |
| **Communication weight** | Lower (as long as 2+/4) | Higher — process matters as much as code |
| **Follow-ups** | Rare | Common — "Now remove that assumption" |
| **Performance threshold** | 68th percentile (2022) | 78th percentile (2025) — candidates must outperform higher |

### Pattern Frequency Surge (2025 Data from interviewing.io)

| Pattern | YoY Change | Onsite Frequency | Key Companies |
|---------|-----------|------------------|---------------|
| Sliding Window | +100% | Very High | Amazon, Google |
| BFS/DFS (Graph) | +80% | Very High | Meta, Google, LinkedIn |
| Trie | +183% | Rising rapidly | Google, Amazon |
| Union-Find | +70% | Moderate-High | Google, Amazon |
| Segment Tree | +400% | Rising (L6+) | Google |
| Dynamic Programming | Decreased | Still High overall | Google, Amazon (Meta bans DP) |
| Binary Search | Stable | High | All |
| Backtracking | Moderate growth | Moderate-High | Meta (AI round), Google |

### Company Coding Styles

| Company | Style | Difficulty | Key Preference |
|---------|-------|-----------|----------------|
| **Amazon** | LP-integrated, OOP + algorithms | LC Medium-Hard | Graphs, DP, concurrency. LPs woven into coding rounds |
| **Meta** | Speed-oriented, two-track | LC Easy-Medium (standard), Med-Hard (AI round) | BFS/DFS, arrays. **NO dynamic programming** |
| **Google** | Theoretical, layered complexity | LC Medium-Hard to Hard | DP, Trie, Segment Tree. Disguised problems, added constraints |
| **Apple** | Correctness-focused | LC Medium (strict quality) | Clean code, memory behaviour, boundary handling |
| **Microsoft** | Org-dependent, fundamentals | LC Medium | Arrays, trees, hash maps |
| **Stripe** | Practical engineering, APIs | Not LC-based | HTTP, JSON, error handling, real APIs. Code quality over speed |

### Onsite Coding for Non-Traditional Roles

| Role | Format | What's Different |
|------|--------|-----------------|
| **Security** | Find-the-vulnerability, secure code review, CTF-style | Algorithms present but easier; replaced partially by security-specific assessment |
| **Frontend** | Build UI components (vanilla JS), DOM manipulation, widgets | Less algorithms, heavy on domain knowledge and practical implementation |
| **ML** | Implement gradient descent from scratch, feature engineering | Blend of algorithmic + domain-specific ML implementation |
| **Data** | SQL deep-dives (window functions, CTEs, optimisation) | SQL replaces much of algorithmic coding |
| **Infra/SRE** | Scripting, automation, system debugging scenarios | "Debug this production issue" live exercise |
| **Mobile** | Platform-specific (Swift/Kotlin), architecture patterns, memory management | Platform lifecycle, offline-first, concurrency models |

---

## Part 4: The Debrief — What You Never See

### How Decisions Are Actually Made

| Company | Who Decides | Method | Veto Power | Timeline |
|---------|------------|--------|------------|----------|
| **Amazon** | Interview panel + Bar Raiser | Consensus via debrief (votes can change) | Bar Raiser + Hiring Manager | 5-14 business days |
| **Google** | Hiring Committee (strangers who never met you) | Consensus (not majority) | HC can request more interviews | 1-2 weeks + team matching |
| **Meta** | Async reviewer panel | Confidence-weighted feedback | Jedi failure = auto reject | 1-2 weeks |
| **Apple** | Hiring Manager | Informal thumbs-up/down | Hiring Manager | Days to 1-2 weeks |
| **Microsoft** | AA Interviewer | AA can override earlier feedback | AA (either direction) | 1-2 weeks post-AA |
| **Netflix** | Informal discussion with directors | Binary pass/fail | Directors | Days |

### The "Mixed Signals" Problem

- Acing coding but bombing system design does NOT automatically disqualify — committees assess holistically
- At Google, mixed feedback may result in additional assessment rounds rather than rejection
- Interviewers seek harmony: "Nobody wants to be the one blocking a hire if everyone else is positive"
- Interviewer track records are maintained — a tough interviewer's "lean no-hire" carries less weight

### What Tips the Balance

- **Amazon:** Problematic Leadership Principles at debrief = "almost always a no hire" regardless of technical strength
- **Google:** A single Strong Hire is more powerful than multiple Leaning Hires
- **Meta:** System design + behavioural determine level. Coding is a binary pass/fail gate
- **Netflix:** System design performance is the primary differentiator

---

## Part 5: The Multi-Round Survival Meta-Game

### Energy Management

**Pre-interview (30-60 min before):**
- Light exercise (walk, not intense)
- Protein-rich meal (avoid heavy carbs)
- 5-minute breathing exercise

**Between rounds:**
- ALWAYS take offered breaks — easier to maintain energy than regain it
- Step away from screens entirely
- 5-minute walk or breathing exercise
- Small energy snack (nuts, fruit — avoid sugar spikes)
- Do NOT review notes — let your brain rest

**The lunch question:**
- **Apple:** Lunch IS the interview — employees will ask questions. Be "on"
- **Google:** Lunch buddy is NOT formally evaluating (unless something egregious)
- **Netflix:** Take the 2-day split if offered

### Recovering After a Bad Round

1. Physical reset: bathroom, splash water, 5 deep breaths
2. Cognitive reframe: rounds are scored independently. The next interviewer does NOT know you struggled
3. Spend zero mental energy replaying it — you cannot change it
4. Treat each round as the first

**Key data:** 75% of candidates show substantial performance variation across rounds. A bad round is statistically normal, not fatal.

### Primacy and Recency Effects in the Loop

First and last rounds carry disproportionate weight in debriefs:
- **First round** sets the initial impression others compare against
- **Last round** is freshest in memory during debrief
- Middle rounds blend together unless something extraordinary happened
- **Strategy:** If you can influence scheduling, place your strongest areas first and last

---

## Part 6: Predicting Your Onsite Questions

### By Company Domain

| Company | Likely System Design Topics |
|---------|-----------------------------|
| Amazon | Order management, warehouse routing, recommendation engine, delivery optimisation |
| Meta | News feed, messaging, live streaming, content moderation at scale |
| Google | Search ranking, distributed file system, ad serving, real-time analytics |
| Netflix | Video streaming CDN, recommendation engine, content encoding pipeline |
| Stripe | Payment processing, fraud detection, API gateway, webhook delivery |
| Anthropic | LLM inference serving, distributed search, GPU memory optimisation |

### By Interviewer Research

- Check LinkedIn for their team/product area
- Read their blog posts, conference talks, GitHub contributions
- Interviewers often ask about topics they've published on
- If they work on search infra, expect search-related questions

### By Glassdoor Intelligence

- Filter by company + exact role + most recent 6 months
- The same question appearing 3+ times means it's in rotation
- Note format changes — companies update processes quarterly

### By Recruiter Intel

Ask BEFORE the onsite:
- "What should I focus preparation on?"
- "Are there specific technical areas the team is looking for?"
- "How many rounds, and what does each cover?"
- "Will there be system design? At what level of abstraction?"
- "Who will be interviewing me?" (enables LinkedIn research)

---

## Part 7: Social Engineering the Onsite

### Building Rapport (First 2 Minutes of Each Round)

- Reference something specific from the interviewer's work — but keep it natural
- Mirror their energy level (casual→casual, formal→formal)
- "I read your team's blog post about [X] — the approach to [Y] was interesting"

### Steering System Design Toward Strengths

- During requirements, ask clarifying questions that guide toward your expertise
- "Should I focus on the data layer or the API design?" — choose your strength
- Proactively offer: "I have experience building something similar"
- When choosing which component to deep-dive, pick the one you know best
- **The system design interview is candidate-led** — leverage this

### Using the Company's Own Problems

- Reference engineering blog posts as design precedent
- Use their product as your example: "If we were building this for [their product]..."
- This demonstrates genuine interest AND anchors your design in their architecture

### The Reverse Interview Time

Last 5 minutes of each round — your impression slot:
- "What's the biggest technical challenge your team is facing?"
- "What are you most excited about for the next six months?"
- Relate answers to your experience
- Avoid generic questions (work-life balance, perks)

---

## Part 8: Post-Onsite Tactics

### Thank-You Emails

- Within 2 hours. Individual emails (NOT bulk). 3-5 sentences
- Reference specific conversation points from YOUR round with THAT interviewer
- **57% of candidates don't send them** — free differentiation
- More impactful at companies where interviewer = decision-maker (Apple, startups). Less impactful at Google (committee decides)

### Team Matching (Google, Meta)

- **Google:** After HC approval, recruiter proposes teams. "Speed dating" with hiring managers. Can take days to months
- **Meta:** Post-onsite matching. Hiring managers more honest about timelines than recruiters

### Managing Multiple Offers

- Aim for all onsites within a 2-week window to create natural urgency
- Inform recruiters you're in "final stages" with other companies
- The initial offer is NEVER the best — always negotiate
- At Meta, revealing a competing offer can increase the offer by $100K+
- Never accept within the recruiter's artificial deadline — ask for more time

### Cooldown Periods After Rejection

| Company | Cooldown | Notes |
|---------|----------|-------|
| Amazon | 6-12 months (up to 24 for poor performance) | Decided by the loop |
| Google | 6-12 months (Strong No-Hire can freeze for years) | Previous feedback carries forward |
| Meta | 6-12 months | Different role may have shorter cooldown |
| Apple | 6 months | |
| Microsoft | No formal cooldown | Can apply to multiple teams in parallel |
| Stripe | 6-12 months | |

### Requesting Feedback

- **Meta:** Company policy — no feedback provided
- **Google:** Recruiter can share which areas were weak
- **Amazon:** Recruiters may share which LPs were flagged
- **Strategy:** Ask specifically: "Was it coding, system design, or behavioural?"

---

## Part 9: 2025-2026 Evolution

### AI Is Changing the Onsite

- **Meta pioneering AI-assisted coding** (Oct 2025) — multi-file projects with embedded AI
- **Google returning to in-person** to counter AI cheating
- **Cheating doubled:** 15% → 35% (June-Dec 2025). Detection accuracy: 85% → 97%
- **The bar rose 15%** — candidates need 78th percentile (up from 68th in 2022)
- **58% of FAANG interviewers adjusted question types** in response to AI
- **75% believe AI lets weaker candidates pass phone screens** — making onsite the true filter

### What Hasn't Changed

- System design fundamentals remain constant — the framework works
- Communication quality still differentiates at L5+
- Practice volume still correlates most strongly with success (5+ mock interviews doubles pass rate)
- No FAANG company has eliminated algorithmic coding questions

---

## Quick Reference — Pre-Onsite Checklist

```
□ Company loop structure confirmed (how many rounds, what each covers)
□ Interviewer names researched on LinkedIn (teams, interests, publications)
□ Company engineering blog read (last 3-5 posts relevant to role)
□ Glassdoor reports reviewed (last 6 months, exact role)
□ Recruiter asked: round breakdown, technical focus areas, interviewers
□ System design: 10-15 questions practiced with full framework (requirements → trade-offs)
□ Coding: 50+ problems at target difficulty, focused on company-preferred patterns
□ Domain-specific prep complete (security/ML/frontend/etc. if applicable)
□ CARL stories ready for behavioural components embedded in technical rounds (Amazon)
□ Back-of-envelope numbers memorised (QPS, latency, storage)
□ Energy plan: meals, snacks, break strategy, 2-day split if offered
□ Thank-you email templates drafted (fill in specifics after each round)
□ Reverse interview questions prepared (company-specific, not generic)
□ Competing offer timelines aligned (if applicable)
```

---

## Sources

### System Design
- [interviewing.io — Senior Engineer's Guide to System Design](https://interviewing.io/guides/system-design-interview) — Core framework, green/red flags, 15 fundamental concepts
- [HelloInterview — Delivery Framework](https://www.hellointerview.com/learn/system-design/in-a-hurry/delivery) — Time-phased framework, requirements gathering
- [HelloInterview — Level Expectations](https://www.hellointerview.com/blog/the-system-design-interview-what-is-expected-at-each-level) — Breadth/Depth/Proactiveness by level
- [DesignGurus — L5 vs L6 Grading](https://designgurus.substack.com/p/i-graded-3-system-design-answers) — Rubric with percentage weights
- [SystemDesignHandbook — Complete Guide 2026](https://www.systemdesignhandbook.com/guides/system-design-interview/) — RESHADED framework, SPARCS non-functionals
- [HackerNoon — Meta SD Interviews (ex-Meta interviewer)](https://hackernoon.com/i-led-dozens-of-meta-system-design-interviews-heres-the-right-way-to-prep) — Meta format, Pirate vs Pirate X
- [HelloInterview Substack — Modern Hardware Numbers](https://hellointerview.substack.com/p/modern-hardware-numbers-for-system) — Updated capacity numbers

### Onsite Coding
- [interviewing.io — You Now Need to Do 15% Better](https://interviewing.io/blog/you-now-need-to-do-15-percent-better-in-technical-interviews) — ITIB Index, 78th percentile bar
- [interviewing.io — Performance Is Arbitrary](https://interviewing.io/blog/technical-interview-performance-is-kind-of-arbitrary-heres-the-data) — 75% volatility, 22% failure rate for strong candidates
- [interviewing.io — How AI Is Changing Interviews](https://interviewing.io/blog/how-is-ai-changing-interview-processes-not-much-and-a-whole-lot) — Zero FAANG eliminated algorithms, cheating data
- [HelloInterview — Meta AI-Enabled Coding](https://www.hellointerview.com/blog/meta-ai-enabled-coding) — Three-phase breakdown, AI degradation
- [LeetCode Discuss — 2025 Most Asked](https://leetcode.com/discuss/post/7417074/) — Pattern frequency data

### Loop Structure & Debrief
- [interviewing.io — Amazon Hiring Process](https://interviewing.io/guides/hiring-process/amazon) — Full loop, Bar Raiser, pre-brief/debrief
- [interviewing.io — Meta Hiring Process](https://interviewing.io/guides/hiring-process/meta-facebook) — Async debrief, confidence scoring, 55% down-levelling
- [interviewing.io — Google Hiring Process](https://interviewing.io/guides/hiring-process/google) — HC packet, scoring paradox, team matching
- [interviewing.io — Apple Hiring Process](https://interviewing.io/guides/hiring-process/apple) — Pair interviewing, lunch evaluation, no standardisation
- [interviewing.io — Netflix Hiring Process](https://interviewing.io/guides/hiring-process/netflix) — 8 rounds, director involvement, Dream Team
- [Candor — Google's Hiring Committee](https://candor.co/articles/interview-prep/google-s-hiring-committee-all-the-deets) — Committee composition, consensus requirement, interviewer track records
- [Medium — Memoirs of an Amazon Bar Raiser](https://medium.com/geekculture/memoirs-of-an-amazon-bar-raiser-718e36241310) — Insider perspective, data-driven debrief
- [Microsoft DevBlogs — The As-Appropriate Interviewer](https://devblogs.microsoft.com/oldnewthing/20231017-00/?p=108897) — AA role, override authority
- [interviewing.io — How to Negotiate with Meta](https://interviewing.io/blog/how-to-negotiate-with-meta) — $100K+ increases with competing offers

### Non-Traditional Roles
- [Frontend Interview Handbook — System Design](https://www.frontendinterviewhandbook.com/front-end-system-design) — RADIO framework
- [GitHub — ML System Design Guide](https://github.com/alirezadir/Machine-Learning-Interviews/blob/main/src/MLSD/ml-system-design.md) — 9-step ML framework
- [GitHub — Mobile System Design](https://github.com/weeeBox/mobile-system-design) — Mobile-specific constraints
- [GitHub — Security Engineering Interview Notes](https://github.com/gracenolan/Notes/blob/master/interview-study-notes-for-security-engineering.md) — Google security format
- [Exponent — Security Engineer Interview Prep](https://www.tryexponent.com/blog/security-engineer-interview-prep) — STRIDE/SALT for security SD

### Post-Onsite
- [LeetCode Discussion — FAANG Cooldown Periods](https://leetcode.com/discuss/post/771157/cool-down-period-for-all-faangs-number-of-tries-and-different-job-posts/) — Compiled cooldown data
- [EvoHire — Preventing AI Cheating 2026](https://www.evohire.ai/post/how-to-prevent-ai-cheating-in-2026-technical-interviews) — Cheating doubling, detection accuracy
- [InterviewQuery — AI Interview Trends 2025](https://www.interviewquery.com/p/ai-interview-trends-tech-hiring-2025) — In-person rise, company policy divergence
