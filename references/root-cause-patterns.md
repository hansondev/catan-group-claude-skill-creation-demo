# Root Cause Patterns Reference

Load this file when completing Section 2 (Root Cause Signals) of the diagnosis. It maps common stated asks to their likely underlying problems in automation advisory work. Use it to pattern-match quickly and form your working hypothesis — but always rate each signal against the specific client input, not just the pattern alone.

---

## Table of Contents

1. [CRM and Pipeline Patterns](#1-crm-and-pipeline-patterns)
2. [Reporting and Visibility Patterns](#2-reporting-and-visibility-patterns)
3. [Manual Work and Efficiency Patterns](#3-manual-work-and-efficiency-patterns)
4. [Integration and Data Flow Patterns](#4-integration-and-data-flow-patterns)
5. [Scoring and Qualification Patterns](#5-scoring-and-qualification-patterns)
6. [How to Use These Patterns](#6-how-to-use-these-patterns)

---

## 1. CRM and Pipeline Patterns

### "We want to push leads into our CRM automatically"

**Most likely root cause:** Leads are not reaching the CRM at all, or are reaching it in an inconsistent state that makes them unusable.

Ask yourself:
- What percentage of leads actually make it into the CRM today?
- If < 80%, the intake process is broken before the automation question even applies.
- If > 80%, the real problem may be data quality or routing, not volume.

**Common underlying failures:**
- No single intake channel — leads arrive via email, trade show badge scans, web forms, referral emails, LinkedIn DMs, and nobody owns aggregating them
- Manual entry fatigue — the person responsible for CRM entry is also doing five other things, so leads pile up and many never get entered
- Duplicate fear — reps don't enter a lead because they're not sure if it's already there, and creating a duplicate feels worse than doing nothing
- Field friction — the CRM form requires 12 fields and reps only know 3 of them, so they don't start

**What this means for Section 3:** The opportunity is not "better automation" — it's "leads that currently fall through the floor." Quantify the gap (% not entering CRM × lead volume × estimated close rate).

---

### "Our CRM data is messy and we want to clean it up"

**Most likely root cause:** No input validation at entry point. Data is being entered manually without constraints, or imported from sources with incompatible schemas.

**Common underlying failures:**
- Same company entered 40 different ways (abbreviations, legal names, trading names, typos)
- Contact records without companies, company records without contacts — orphaned data
- Duplicate contacts from different import sources (CSV, form, manual entry all creating separate records)
- Status fields left blank because nobody agreed on what they mean

**What this means for the plan:** A one-time data clean is not the answer — the mess will return within 3 months. The fix is at the entry point: normalisation, deduplication, and field validation before data touches the CRM.

---

### "We need a scoring model to prioritise which leads to call"

**Most likely root cause:** The sales team doesn't have enough signal to know which leads to prioritise, AND the CRM data is too inconsistent to score reliably.

**Distinguish between:**
- **Volume problem:** Too many leads, need to rank them. Scoring is the right answer here — but only if the data quality is high enough to score reliably.
- **Data quality problem:** The scoring model fails because half the firmographic fields are empty or wrong. Building scoring on top of bad data produces a model nobody trusts within 4 weeks.
- **Process problem:** Leads exist in the CRM but nobody is working them systematically. Scoring won't fix a follow-up cadence problem.

**Diagnostic question:** "If I showed your team a score of 87 for a lead, would they trust it enough to act on it?" If the answer is "probably not", the data quality problem comes first.

---

## 2. Reporting and Visibility Patterns

### "We want a dashboard showing pipeline health"

**Most likely root cause:** Leadership does not trust the data in the CRM, so they want a visual layer on top of it. But the visual layer inherits the same data quality problems.

**Common underlying failure:** Nobody is updating the CRM consistently, so the pipeline view is always out of date. The request for a dashboard is actually a request for someone to fix the CRM hygiene problem.

**What to surface:** "Before we build a dashboard, can you tell me what percentage of your current pipeline you'd estimate is accurately reflected in the CRM right now?" If the answer is below 70%, a dashboard is premature.

---

### "We need automated weekly reports to go to leadership"

**Most likely root cause:** Someone is spending 2-4 hours every Friday manually pulling numbers from 3 different systems. The data exists but the aggregation is manual.

**This is usually the right ask** — it's one of the few cases where the stated ask and root cause are aligned. The risk is over-engineering: leadership often wants a simple number (this week's new leads, this week's qualified, this week's closed), not a 20-metric dashboard.

**Check before building:** "What does the current manual report look like? Can I see last week's version?" This tells you the exact format and fields before you architect anything.

---

## 3. Manual Work and Efficiency Patterns

### "We want to automate our onboarding process"

**Most likely root cause:** The onboarding process is undocumented — people are doing it from memory, differently every time. Automating an undocumented process just makes the inconsistency faster.

**Prerequisite check:** Ask to see the current onboarding checklist or SOP. If one doesn't exist, the first week of the engagement is documenting the current process, not building automation.

**Common trap:** Client shows you what they *want* onboarding to look like, not what it actually looks like today. Build against the current reality, then improve it.

---

### "Our team spends too much time on manual data entry"

**Most likely root cause:** Either the source data doesn't exist in a machine-readable form (paper forms, phone calls, verbal handoffs) — in which case the fix is upstream — or the data exists but there's no integration between the source system and the destination.

**Distinguish:**
- Source data is already digital → integration problem, solvable with n8n
- Source data requires human interpretation → automation can assist but not replace
- Source data is on paper → digitise first, then automate

---

### "We want to reduce response time to inbound leads"

**Most likely root cause:** Leads are landing in a shared inbox with no routing, triage, or SLA. They sit until someone picks them up.

**The fix is usually routing before automation:** Which team member handles which type of lead? What's the SLA? What happens if nobody picks it up in 2 hours? Answer these questions first, then build the routing automation. Building a notification system without a routing logic just creates noise.

---

## 4. Integration and Data Flow Patterns

### "We want our tools to talk to each other"

**Most likely root cause:** There are 2-3 specific data flows the team needs but they've described it as a general integration problem because they don't know which ones matter most.

**Diagnostic move:** Ask them to walk through one real work scenario — "tell me what happens from the moment a new lead arrives to when it's worked by sales." The specific friction points will appear in this walkthrough. Solve those three points, not "integration in general."

---

### "We want to migrate from [Tool A] to [Tool B]"

**Most likely root cause:** The team is frustrated with Tool A and hoping Tool B is better. The real problem may be process, not tool.

**Before scoping the migration, check:**
- What specifically is broken in Tool A? (Feature limitation? Adoption? Cost?)
- Have you trialled Tool B? What did the trial show?
- Are the problems with Tool A actually Tool A problems, or process/behaviour problems that will follow the team into Tool B?

A migration is 3× more expensive than the client expects. If the root cause is behaviour, a migration doesn't fix it.

---

## 5. Scoring and Qualification Patterns

### "Our scoring model isn't working"

**Most likely root cause:** One of three things, in decreasing order of probability:
1. **Data quality** — the fields the model uses are empty or inaccurate for too many records
2. **Definition mismatch** — "qualified" means something different to sales than to marketing; the model is scoring against the wrong definition
3. **Actual model problem** — the weights or criteria genuinely don't reflect conversion patterns

**Diagnostic check:** Pull the last 30 leads the model scored as High. How many of them closed or became active opportunities? If < 50%, the model criteria are wrong. If the sample is too small to know, the data volume is the problem.

---

### "We want to enrich our leads with company data"

**Most likely root cause:** Enrichment is the right idea if the underlying issue is that reps are making call/no-call decisions without enough context. But enrichment only helps if reps actually look at the enriched data before acting.

**Check adoption before API cost:** "When a lead has company size, industry, and revenue already populated in the CRM, does your team actually use that to decide how to prioritise?" If the answer is "sometimes" or "not really", solve the follow-up process before paying for enrichment.

---

## 6. How to Use These Patterns

1. Read the stated ask first (Section 1 of the diagnosis).
2. Scan this reference for the closest pattern match.
3. Use the pattern's "common underlying failures" as a checklist — which ones appear in the client input?
4. Rate each signal High / Medium / Low based on evidence in the client input, not just pattern match.
5. Form a working hypothesis from the pattern + the specific evidence.

**Important:** These patterns reflect the most common cases. They are starting points, not verdicts. A client who says "we want to push leads into the CRM" might genuinely just need the integration — if their intake is already working and their CRM data is clean. Read the input before reaching for the pattern.
