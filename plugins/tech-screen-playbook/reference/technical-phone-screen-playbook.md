# Technical Phone Screen Playbook: Category-Aware Preparation Guide

## Overview

This document is a comprehensive, category-aware playbook for acing technical phone screens in tech company interview pipelines. The technical phone screen is the live coding/technical assessment — typically 45-60 minutes on CoderPad/HackerRank where you solve problems while explaining your thought process. Unlike the recruiter and HM screens (which are conversational), this is where you demonstrate you can actually do the work.

This playbook is organised by **job category** because technical phone screens vary dramatically by role type. A security engineer's screen looks nothing like a frontend engineer's. The universal framework applies to all categories; the category-specific sections provide the exact domains, question types, and preparation strategies for each.

**What IS covered:** Universal meta-skills (thinking out loud, time management, handling being stuck), interview rubrics with quantitative data from 100K+ interviews, and deep breakdowns for 10 job categories: Backend, Frontend, Security, Data Engineering, ML/AI, Infrastructure/DevOps/SRE, Mobile, Full-Stack, Cloud Architecture, and Embedded Systems.

**What is NOT covered:** Recruiter screens (see `recruiter-screen-playbook.md`), hiring manager screens (see `hiring-manager-screen-playbook.md`), system design deep-dives, or post-offer negotiation.

**Research date:** March 2026.

---

## Part 1: Universal Framework (All Categories)

### What Interviewers Actually Evaluate

Data from 100,000+ interviews on interviewing.io reveals a four-dimension rubric used across FAANG:

| Dimension | What It Measures | Weight (L3-L4) | Weight (L5+) |
|-----------|-----------------|-----------------|---------------|
| **Problem Solving (Solve)** | Understanding the problem, approach, trade-off analysis, optimisation | Highest | Highest |
| **Technical Competency (Code)** | Speed, accuracy, fluency, clean implementation | Highest (tied) | High |
| **Communication** | Explaining approach, clarifying assumptions, narrating decisions | Low (as long as 2+/4) | High — becomes critical |
| **Testing** | Edge cases, self-correction, bug detection, validation | Moderate | Moderate |

**The quantitative reality:**
- Dropping 1 point from Code or Solve causes rejection rates to skyrocket **6x**
- Dropping 1 point from Communicate has "by far the smallest" negative impact at L3-L4
- At L5+: communication matters significantly more
- Strong candidates (mean score 3.0/4) still **fail 22% of the time** — single interviews are noisy
- Having seen the question before gives a **+16.6% advantage** (p<0.001) — pattern recognition from practice is real
- **5+ practice interviews double pass rates**

**Company philosophies:**

| Company | Philosophy | What This Means |
|---------|-----------|-----------------|
| **Meta** | "What" company — results-oriented | Wants optimal solutions quickly |
| **Google** | "How" company — process-oriented | Prioritises thought process over perfect answers |
| **Amazon** | "What" company with LP overlay | Results-focused, team-dependent variation |
| **Microsoft** | "How" company — high variability | Evaluates how you think, varies across teams |

### The 5 Meta-Skills

#### 1. Thinking Out Loud

The 5 common failure modes (from analysis of 600+ interviews):

1. **Jumping into code too soon** — Candidates spend <30 seconds on design. Fix: Allocate ~5 min for high-level design BEFORE writing code
2. **Communicating half-thoughts** — "Hmm, I wonder if... no, never mind." Fix: Fully articulate approaches you're considering and why you're eliminating them
3. **Not asking clarifying questions** — Fix: Ask about constraints, input size, edge cases, data structure assumptions
4. **Assuming the interviewer controls all rules** — Fix: Proactively set expectations: "My process is to think, plan, code, then test. Does this work for you?"
5. **Not asking for help soon enough** — Silent struggling is worse than a hint with a score deduction

#### 2. Time Management (45-60 Minutes)

| Phase | Time | Activity |
|-------|------|----------|
| Introduction | 2-3 min | Greetings, context |
| Clarifying questions | 3-5 min | Constraints, edge cases, input/output format |
| High-level design | 5 min | Approach selection, complexity analysis |
| Implementation | 20-30 min | Write code, narrate as you go |
| Testing & debugging | 5-10 min | Walk through examples, edge cases, fix bugs |
| Optimisation discussion | 3-5 min | Better approaches, trade-offs |
| Candidate questions | 3-5 min | Questions for the interviewer |

#### 3. Handling Being Stuck

Escalation ladder:
1. **State the gap clearly:** "I need to find X. I can do Y. The gap is connecting them."
2. **Solve a simpler version:** Remove one constraint
3. **Start with brute force:** Even O(n³) is better than nothing
4. **Mine problem details:** If the input is sorted, the interviewer said so for a reason
5. **Ask a targeted hint:** "I'm stuck on the overlapping intervals case. Could you point me in the right direction?"

#### 4. Code Quality That's Measurably Rewarded

From analysis of thousands of interviews:
- Successful candidates write **16% more code** (2,045 chars avg vs 1,760)
- Successful candidates define **22% more functions** (3.29 avg vs 2.71 in Python)
- **No significant language advantage** (except Java at Java companies: +3.7%)
- **Fluency matters more than language choice** — use what you're fastest in

#### 5. Testing During the Interview

- Walk through code with a **concrete example** (not the trivial case)
- Test **edge cases**: empty input, single element, duplicates, negatives, overflow
- **Trace line by line**, updating variables mentally
- Successful interviews produce error-free code **64% of the time** vs 60% for unsuccessful

### Common Formats

| Format | Description | Preparation |
|--------|-------------|-------------|
| **Live coding (CoderPad/HackerRank)** | 1-2 algorithmic problems, shared IDE | LeetCode, practice on actual platforms |
| **System design (high-level)** | Design a simplified system in 30-45 min | Study patterns, practice diagramming |
| **Debugging** | Find and fix bugs in provided code | Practice reading unfamiliar code |
| **Code review** | Review a PR, identify issues | Study code smells, security vulns, performance |
| **Take-home + discussion** | Build something offline, defend live | Clean code, tests, documentation |
| **Pair programming** | Collaborative coding with interviewer | Narrating decisions, accepting feedback |

---

## Part 2: Category-Specific Breakdowns

### Category 1: Backend / Server-Side Engineering

**Domains tested:** Data structures & algorithms (arrays, trees, graphs, hash maps, heaps), system design (URL shortener, rate limiter, chat), API design (REST conventions, pagination, idempotency), database fundamentals (indexing, normalisation, SQL vs NoSQL), concurrency (race conditions, locks, deadlock prevention).

**Common questions:**
- "Design a URL shortener" / "Implement an LRU cache" / "Design a rate limiter"
- "How would you handle a slow API endpoint?"
- "What is a race condition and how do you prevent it?"

**Level signals:**

| Level | What It Sounds Like |
|-------|-------------------|
| Mid | "I implemented the caching layer using Redis with a 30-minute TTL" |
| Senior | "We chose Redis over Memcached because we needed persistence, and the TTL was calibrated against P95 cache hit rates" |
| Staff | "This was part of a broader initiative across 4 teams. I wrote the RFC and we reduced P99 from 450ms to 120ms across 500M daily transactions" |

**Staff differentiators:** Talk as a peer, focus on the genuinely hard parts, design simple systems ("Where does this NOT need to scale?"), make decisive choices with justification.

---

### Category 2: Frontend / UI Engineering

**Domains tested:** JavaScript fundamentals (closures, prototypes, `this`, event loop, promises, async/await), DOM manipulation and event delegation, CSS layout (Flexbox, Grid, responsive), React patterns (hooks, state management, reconciliation), browser APIs, accessibility (ARIA, semantic HTML, keyboard nav), performance (code splitting, lazy loading, Core Web Vitals).

**Common questions:**
- "Implement a debounce function" — closure + timer fundamentals
- "Build a todo list / autocomplete / infinite scroll" — practical UI
- "Explain the event loop" — conceptual deep-dive
- "What happens when you call setState?" — React internals
- CSS: "Center a div" / "Responsive layout without media queries"

**Common gotchas:** Not knowing `==` vs `===`, misunderstanding `this` in arrow functions, ignoring accessibility, forgetting to clean up effects in useEffect, not handling loading/error states.

**Preparation:** [GreatFrontEnd](https://www.greatfrontend.com/), [Frontend Interview Handbook](https://www.frontendinterviewhandbook.com/).

---

### Category 3: Security Engineering / AppSec / Cybersecurity

**This category is structurally different from SWE interviews.** Security screens blend conceptual knowledge, hands-on skills, scenario reasoning, and coding. Format: behavioural intro (5 min) → conceptual deep-dive (20-30 min) → scenario questions (10-15 min) → optional code review (10-15 min).

#### OWASP Top 10 (Must Know Cold)

| Vulnerability | Attack Mechanism | Remediation |
|--------------|-----------------|-------------|
| **SQL Injection** | User input concatenated into SQL queries | Parameterised queries / prepared statements |
| **XSS** | Malicious script injected via user input, executed in victim's browser | Output encoding, CSP headers, input validation |
| **CSRF** | Forged requests from authenticated user's browser | Anti-CSRF tokens, SameSite cookies |
| **Broken Authentication** | Weak credentials, session fixation, missing MFA | MFA, secure session management, account lockout |
| **SSRF** | Server makes requests to attacker-controlled URLs | Input validation, allowlisting, network segmentation |
| **Insecure Deserialization** | Untrusted data deserialised leading to RCE | Don't deserialise untrusted data; use JSON |
| **XXE** | Malicious XML references external entities | Disable DTD processing, use JSON |
| **Broken Access Control** | Horizontal/vertical privilege escalation | RBAC, server-side auth checks |
| **Security Misconfiguration** | Default creds, unnecessary services, verbose errors | Hardening guides, automated scanning |
| **Cryptographic Failures** | Weak algorithms, plaintext storage, missing encryption | AES-256 at rest, TLS 1.2+ in transit, proper key management |

#### Threat Modeling (STRIDE)

- **S**poofing — Can an attacker impersonate a user/service?
- **T**ampering — Can data be modified in transit or at rest?
- **R**epudiation — Can actions be denied without audit trail?
- **I**nformation Disclosure — Can sensitive data leak?
- **D**enial of Service — Can the system be overwhelmed?
- **E**levation of Privilege — Can a low-privilege user gain admin?

#### Cryptography Fundamentals

| Concept | What You Must Know |
|---------|-------------------|
| Symmetric vs Asymmetric | AES (1 key) vs RSA/ECDHE (key pair). When to use each |
| Hashing vs Encryption | Hashing is one-way (bcrypt, SHA-256); encryption is reversible. Never hash passwords with MD5/SHA1 |
| TLS 1.3 Handshake | Client Hello → Server Hello → certificate → key agreement → symmetric session. 1-RTT, mandatory PFS |
| Perfect Forward Secrecy | Ephemeral keys (ECDHE) so compromising long-term key doesn't decrypt past sessions |
| Key Management | HSMs, key rotation, envelope encryption, never store keys alongside data |

#### Incident Response (NIST Lifecycle)

**Preparation → Detection & Analysis → Containment → Eradication → Recovery → Lessons Learned**

Expect: "A developer's laptop was compromised. Walk me through your response." / "You discover data exposed in a public S3 bucket. What do you do?"

#### Cloud Security

| Domain | Key Topics |
|--------|-----------|
| **IAM** | Least privilege, RBAC, MFA, service accounts, assume-role |
| **Data Protection** | AES-256 at rest, TLS in transit, confidential computing |
| **Network** | Security groups, NACLs, VPC design, private subnets |
| **Logging** | CloudTrail, CloudWatch, SIEM, GuardDuty |
| **Container Security** | Image scanning, pod security, secrets injection |
| **DevSecOps** | SAST/DAST in CI/CD, IaC scanning, shift-left |

#### Security Subdomain Differences

| Subdomain | Phone Screen Focus |
|-----------|-------------------|
| **Red Team / Offensive** | Exploitation techniques, Metasploit, Burp Suite, OSINT, social engineering |
| **Blue Team / Defensive** | SIEM/SOC, log analysis, detection engineering, incident response |
| **AppSec** | OWASP deep-dive, secure code review, SDLC integration, threat modeling |
| **GRC** | Compliance frameworks (SOC 2, PCI DSS, GDPR, HIPAA), audit methodology |
| **Cloud Security** | Cloud-native controls, IAM, IaC security, container security |

#### Level Signals

| Level | Expectation |
|-------|-------------|
| Mid | Knows OWASP Top 10, can explain and remediate, follows playbooks |
| Senior | Knows attack chains, threat models complex systems, mentors, leads IR |
| Staff | Defines security standards, influences org-wide architecture, handles board-level communication |

#### Certifications

| Cert | Impact |
|------|--------|
| **OSCP** | Highest respect from technical interviewers. Proves hands-on offensive skills |
| **CISSP** | Gold standard for senior/leadership. Often a hard requirement for security architect roles |
| **CEH** | Gets past HR filters but low respect from practitioners |
| **Security+** | Entry-level baseline, not differentiating at mid+ |

**IMPORTANT:** 89% of hiring managers won't interview uncertified candidates for security roles.

**Common traps:** Saying "use AES" without explaining key management. Confusing authentication with authorisation. Describing attacks without remediation. Not mentioning defence in depth.

---

### Category 4: Data Engineering

**Domains tested:** SQL deep-dives (window functions, CTEs, query optimisation), ETL/ELT pipeline design (Airflow, Spark, idempotency), data modeling (star schema, slowly changing dimensions), streaming vs batch (Kafka, Flink), data quality.

**Common questions:**
- "Write a query to find the second-highest salary per department" — window functions
- "Design a pipeline for ingesting clickstream data" — Kafka → Spark → warehouse
- "A pipeline is running slowly. Diagnose and fix." — partitioning, indexing, parallelism
- "Explain slowly changing dimensions and how you handle them"

**Strong answer patterns:** Always discuss idempotency, mention monitoring/alerting, address schema evolution, discuss data quality checks (Great Expectations, dbt tests).

---

### Category 5: ML/AI Engineering

**Domains tested:** ML fundamentals (bias-variance, overfitting, cross-validation, regularisation), model selection, feature engineering, ML system design (training pipelines, serving, monitoring), evaluation metrics.

**LLM/GenAI topics (critical for 2025-2026):**

| Topic | What You Must Know |
|-------|-------------------|
| **RAG** | Architecture, chunking, embeddings, vector DBs, reranking, hybrid search |
| **Fine-tuning** | Full vs PEFT (LoRA, QLoRA), when to fine-tune vs prompt engineer vs RAG |
| **Prompt engineering** | Zero-shot, few-shot, chain-of-thought, ReAct |
| **Transformers** | Attention mechanism, positional encoding, tokenisation |
| **Deployment** | Quantisation, distillation, serving infra, latency/throughput trade-offs |

**ML system design framework:** Problem & metrics → Data → Feature engineering → Model selection → Evaluation (offline + online) → Serving (batch vs real-time) → Monitoring & iteration.

---

### Category 6: Infrastructure / DevOps / SRE

**Domains tested:** Linux (process mgmt, permissions, systemd, troubleshooting), networking (TCP/IP, DNS, load balancing L4/L7, CDN), containers (Docker, Kubernetes), CI/CD, monitoring (Prometheus, Grafana, distributed tracing), incident management (SLI/SLO/SLA, error budgets), IaC (Terraform, Ansible).

**Common questions:**
- "A service returns 5xx errors. Walk me through debugging." — real-time troubleshooting
- "How does a K8s pod get scheduled?" — kube-scheduler, resource requests/limits
- "Design a CI/CD pipeline for a microservice" — build, test, scan, deploy, rollback
- "Difference between liveness and readiness probes?"
- "Explain DNS resolution end to end"

**SRE-specific:** SLI/SLO/SLA definitions, error budgets, toil reduction, blameless postmortems.

---

### Category 7: Mobile Engineering (iOS/Android)

**iOS domains:** Swift, SwiftUI/UIKit, GCD/async-await/actors, Core Data, ARC and retain cycles, app lifecycle.

**Android domains:** Kotlin, Jetpack Compose, coroutines/Flow, Room/DataStore, Activity/Fragment lifecycle, ViewModel.

**Common questions:**
- "Explain the app lifecycle"
- "How do you handle memory leaks on your platform?"
- "Design a mobile app with offline-first capability"
- "Optimise a list displaying 10,000 items"
- Architecture: MVVM, Clean Architecture, dependency injection

---

### Category 8: Full-Stack Engineering

**How it differs:** Tests breadth over depth. Integration questions spanning the entire stack.

**Common questions:**
- "Design data model, API endpoints, and UI components for a collaborative document editor"
- "How do you implement optimistic updates in a React frontend with a REST API?"
- "Walk through how a user action in the browser results in a database write — every step"
- Rapid breadth checks: SQL → event loop → CSS specificity → database indexing

---

### Category 9: Cloud / Solutions Architecture

**Domains tested:** Service selection (Lambda vs ECS vs EKS), multi-region and DR (RPO/RTO), cost optimisation, migration strategy (7 Rs), Well-Architected Framework (6 pillars).

**Common questions:**
- "When would you use Lambda vs ECS vs EKS?"
- "Design a data pipeline: Kinesis vs SQS vs EventBridge?"
- "How would you reduce a $50K/month AWS bill by 40%?"
- "Evaluate this architecture against the Well-Architected pillars"

---

### Category 10: Embedded Systems / Firmware

**Domains tested:** RTOS concepts (preemptive vs cooperative scheduling, priority inversion), memory management in constrained environments, volatile keyword (asked in nearly every embedded interview), ISRs, bit manipulation, communication protocols (I2C, SPI, UART, CAN).

**Must-know questions:**
- "What does `volatile` do and when must you use it?" → Prevents compiler caching in registers. Three mandatory cases: memory-mapped registers, ISR-modified globals, shared thread variables
- "Can a variable be both `const` and `volatile`?" → Yes — a read-only hardware status register
- "Can you call printf from an ISR?" → No — not reentrant. Use a flag/buffer instead
- "Why is malloc dangerous in embedded?" → Fragmentation + non-deterministic timing

---

## Part 3: How AI Is Changing Technical Screens (2025-2026)

The landscape is shifting:

- **In-person rounds rose from 24% (2022) to 38% (2025)** — partly to counter AI-assisted cheating
- **43% of companies use AI in hiring** (up from 26% in 2024)
- Some companies (Rippling) explicitly **allow Copilot/ChatGPT** during interviews
- AI/LLM competency in job requirements surged: backend roles 6.7% → 13% requiring AI skills

**What interviewers now evaluate:**
1. **Process over product** — how you reason matters more than final code
2. **Code review ability** — evaluating whether AI-generated code is correct
3. **Architectural judgment** — trade-off analysis that AI can't reliably perform
4. **AI fluency** — can you effectively collaborate with AI tools?

**What hasn't changed:** You still need to write and read code, understand data structures, and communicate your reasoning clearly.

---

## Part 4: Company Size Impact

| Factor | Startup (<50) | Mid-Size (50-500) | Enterprise/FAANG |
|--------|--------------|-------------------|-----------------|
| **Who interviews** | Technical founder directly | Mix of HR + technical manager | Dedicated phone screen pipeline |
| **Question style** | "How would you build X for us?" | Mix practical + standardised | Highly standardised LeetCode/system design |
| **What matters most** | Immediate productivity, breadth | Balance of skills and process | Ability to pass structured evaluation |
| **Take-home vs live** | More likely practical take-home | Varies | Predominantly live coding |

---

## Quick Reference — Pre-Screen Checklist

```
□ Know what format to expect (live coding, system design, take-home discussion, pair programming)
□ Practiced on the actual platform (CoderPad, HackerRank) — not just locally
□ Chose language — the one you're FASTEST and most ACCURATE in
□ Warmed up with 2-3 easy problems (30 min before the screen)
□ Prepared category-specific domain knowledge (see relevant section above)
□ Rehearsed thinking out loud (narrate approach before coding)
□ Prepared clarifying questions to ask before coding
□ Time management plan: 5 min design → 25 min code → 10 min test
□ Quiet environment, stable internet, second screen/notepad for scratch work
□ Water, comfortable chair, do not schedule anything immediately after
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Completely blank on a problem | Say: "Let me think about this from first principles." Start with brute force — any solution beats no solution |
| Running out of time | Communicate: "I see the path to the solution — let me describe my approach and implement the key parts" |
| Interviewer seems unengaged | They may be tired or have a poker face by design. Stay energetic and narrate your thinking regardless |
| Your code has a bug and you can't find it | Trace through with a concrete example. Say: "Let me walk through this with input X." The bug usually reveals itself |
| Asked about a technology you don't know | "I haven't used [X] in production, but I've used [similar Y]. Here's how I'd approach it..." |
| The problem is much harder than expected | This might be intentional — they want to see how you handle difficulty. Get as far as you can and communicate clearly |
| Pair programming and you disagree with the interviewer | Listen, consider their point, and either incorporate it or explain your reasoning. Never get combative |

---

## Sources

- [Tech Interview Handbook — Coding Interview Rubrics](https://www.techinterviewhandbook.org/coding-interview-rubrics/) — Four evaluation dimensions and scoring methods across FAANG
- [interviewing.io — Does Communication Matter? (100K Interviews)](https://interviewing.io/blog/does-communication-matter-in-technical-interviewing-we-looked-at-100k-interviews-to-find-out) — Code vs Solve vs Communicate weighting by level
- [interviewing.io — 600+ Interviews: 5 Common Problem Areas](https://interviewing.io/blog/ive-conducted-over-600-technical-interviews-on-interviewing-io-here-are-5-common-problem-areas-ive-seen) — Concrete failure patterns from an experienced interviewer
- [interviewing.io — Language and Code Style Analysis](https://interviewing.io/blog/we-analyzed-thousands-of-technical-interviews-on-everything-from-language-to-code-style-here-s-what-we-found) — Language selection, code modularity, success correlations
- [interviewing.io — FAANG Hiring Process Guide](https://interviewing.io/guides/hiring-process) — Company philosophies, chaos scores, process details
- [interviewing.io — Performance Is Kind of Arbitrary](https://interviewing.io/blog/technical-interview-performance-is-kind-of-arbitrary-heres-the-data) — Performance volatility across interviews
- [Hello Interview — 5 Keys to Staff-Level System Design](https://www.hellointerview.com/blog/staff-level-system-design) — Senior vs staff differentiators
- [CoderPad — Interview Preparation Guide](https://coderpad.io/resources/docs/for-candidates/interview-preparation-guide/) — Platform tips, time management
- [Interview Cake — Tricks for Getting Unstuck](https://www.interviewcake.com/tricks-for-getting-unstuck-programming-interview) — Strategies for handling being stuck
- [jassics/security-interview-questions (GitHub)](https://github.com/jassics/security-interview-questions/blob/main/application-security-interview-questions.md) — AppSec interview questions with code review examples
- [tadwhitaker/Security_Engineer_Interview_Questions (GitHub)](https://github.com/tadwhitaker/Security_Engineer_Interview_Questions/blob/master/security-interview-questions.md) — Security engineer questions covering crypto, networking, compliance
- [Grace Nolan's Security Engineering Study Notes (GitHub)](https://github.com/gracenolan/Notes/blob/master/interview-study-notes-for-security-engineering.md) — Comprehensive study guide for Google Security interviews
- [Practical DevSecOps — Threat Modeling Questions](https://www.practical-devsecops.com/threat-modeling-interview-questions-and-answers/) — 55 threat modeling questions with answers
- [Frontend Interview Handbook](https://www.frontendinterviewhandbook.com/introduction) — Open-source frontend interview guide
- [GreatFrontEnd — 100 React Interview Questions](https://www.greatfrontend.com/blog/100-react-interview-questions-straight-from-ex-interviewers) — React questions from ex-FAANG interviewers
- [InterviewQuery — Data Engineer Questions (150+)](https://www.interviewquery.com/p/data-engineer-interview-questions) — Data engineering question bank
- [alirezadir/Machine-Learning-Interviews (GitHub)](https://github.com/alirezadir/Machine-Learning-Interviews) — ML interview guide covering system design and fundamentals
- [DataCamp — LLM Interview Questions 2026](https://www.datacamp.com/blog/llm-interview-questions) — 36 LLM-specific questions
- [bregman-arie/devops-exercises (GitHub)](https://github.com/bregman-arie/devops-exercises) — 115+ DevOps questions with solutions
- [weeeBox/mobile-system-design (GitHub)](https://github.com/weeeBox/mobile-system-design) — Mobile system design interview framework
- [RareSkills — 150+ Ethereum Developer Questions](https://rareskills.io/post/solidity-interview-questions) — Blockchain/Solidity interview questions
- [InterviewQuery — AI Interview Trends 2025](https://www.interviewquery.com/p/ai-interview-trends-tech-hiring-2025) — AI/LLM competency surge, in-person round resurgence
- [Formation.dev — What AI Changes in SWE Interviews](https://formation.dev/blog/what-ai-changes-and-doesnt-change-in-swe-interviews/) — How AI shifts evaluation criteria
