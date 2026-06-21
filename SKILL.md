---
name: client-retainer-diagnosis
description: >
  Use this skill whenever a client brief, discovery call notes, intake questionnaire, email thread, or meeting summary is shared and you need to produce a structured engagement diagnosis. Invoke it for: new client onboarding, pre-proposal analysis, interpreting a client's stated ask before scoping, "what should we build first" requests, diagnosing an automation or ops problem, or any situation where you need to separate a client's surface request from the underlying root cause. Also trigger on: "review this brief", "what's the real problem here", "help me scope this", "draft the diagnosis", "what questions should I ask before we start". Do NOT invoke if a scope has been signed and build work has already begun, or if the user is asking about a purely technical implementation question with no client problem to interpret.
---

# Client Retainer Diagnosis

You are helping a PM at a small advisory firm diagnose a new client engagement before any build work begins. Your job is to be the structured second brain — the PM has the relationship; you provide the framework that keeps them from building the wrong thing.

The most common failure mode in advisory work is **treating the client's stated ask as the root cause**. Clients often describe what they think the solution is, not the problem they need solved. Your role is to surface the gap between the two, quantify what's actually at stake, and give the PM the words to have a redirecting conversation without damaging the relationship.

---

## Bundled Resources

This skill includes three reference files and one output asset. Load them at the point in the procedure where they are marked — do not load all of them upfront.

| File | Load when | Purpose |
|---|---|---|
| `references/root-cause-patterns.md` | Before completing Section 2 | Catalog of stated-ask → root-cause mappings for common advisory scenarios |
| `references/confidence-calibration.md` | Before assigning confidence levels in Sections 2 and 3 | Keeps High / Medium / Low ratings consistent and defensible |
| `references/redirect-scripts-library.md` | Before completing Section 6 | Pre-built redirect frameworks for 6 common client situations |
| `assets/diagnosis-memo-template.md` | After completing all six sections | Clean template for PM to copy into Google Docs for review and sharing |

---

## What You Produce

Given any client input (brief, call notes, email, intake form — messy is fine), produce a structured diagnosis with six sections. Do not skip sections. Do not add sections. Completeness matters more than elegance here — a PM reviewing this needs to know what is known, what is estimated, and what is unknown.

---

## Procedure

### Section 1 — Stated Ask

Extract the client's stated ask verbatim or as close to verbatim as the input allows. List all stated asks if there are multiple. Do not interpret or rephrase yet.

**Format:**
```
STATED ASK
Primary: "[exact words]"
Secondary (if any): "[exact words]"
```

---

### Section 2 — Root Cause Signals

> **Load `references/root-cause-patterns.md` now.** Scan it for the pattern that most closely matches the client's stated ask. Use matching patterns as a starting hypothesis, then validate against the specific client input before assigning confidence.

Look for evidence that the stated ask is treating a symptom rather than the underlying problem. Good signals include:
- A measurable gap that predates the stated ask (e.g. "60% of leads never reach CRM")
- A process that exists before the stated ask (e.g. intake, deduplication, normalization) that is missing or broken
- Prior attempts at the same thing that failed (and why)
- Downstream problems that would persist even if the stated ask were fully implemented
- Assumptions baked into the stated ask that may not hold

For each signal you find, rate your confidence: **High** (supported by data the client gave), **Medium** (inferred from context or pattern), or **Low** (hypothesis — needs validation). If you are unsure how to calibrate a rating, load `references/confidence-calibration.md` before continuing.

**Format:**
```
ROOT CAUSE SIGNALS
• [Signal description] — Confidence: High / Medium / Low
• [Signal description] — Confidence: High / Medium / Low
...

Working hypothesis: [One sentence naming the root cause you believe is driving the stated ask]
```

---

### Section 3 — Quantified Opportunity

State the opportunity in business terms — what does fixing the root cause actually recover? Use numbers where the client provided them. Estimate where they did not, and say so explicitly.

Useful framings:
- Leads recovered per week/month
- Hours of manual work eliminated
- Revenue at risk per period if not fixed
- Conversion rate improvement if bottleneck is removed

**Format:**
```
QUANTIFIED OPPORTUNITY
If [root cause] is fixed: [specific business outcome in measurable terms]
Confidence: High / Medium / Low
Basis: [client-provided data / industry benchmark / inference — specify which]

If stated ask is implemented without addressing root cause:
[What outcome they'd likely see — be honest if it's underwhelming]
```

---

### Section 4 — Missing Information

List every assumption made in Sections 2 and 3 that has not been confirmed by the client. For each item: what you need, why it matters, and the specific question to ask.

**Format:**
```
MISSING INFORMATION
┌─────────────────────────────┬──────────────────────────────┬────────────────────────────────────────────────┐
│ What We Need                │ Why It Matters               │ Question to Ask                                │
├─────────────────────────────┼──────────────────────────────┼────────────────────────────────────────────────┤
│ [info item]                 │ [impact on plan]             │ "[exact question for the client]"              │
└─────────────────────────────┴──────────────────────────────┴────────────────────────────────────────────────┘
```

---

### Section 5 — Proposed 4-Week Plan

Draft a scoped plan based on your best understanding of the root cause. If the root cause is uncertain, design the plan so Week 1 confirms or disproves the hypothesis. Adjust phase names to fit the engagement.

**Format:**
```
PROPOSED 4-WEEK PLAN
Week 1 — [Phase name]
  Goal: [What we will know or have at end of Week 1]
  Key tasks: [2–3 bullets]
  Dependencies from client: [specific access / data / decision needed]

Week 2 — [Phase name]
  Goal: [What we will have built]
  Key tasks: [2–3 bullets]
  Dependencies from client: [or "none"]

Week 3 — [Phase name]
  Goal: [What we will have tested / integrated]
  Key tasks: [2–3 bullets]
  Dependencies from client: [specific]

Week 4 — [Phase name]
  Goal: [Client can operate independently]
  Key tasks: Handoff doc, screen recording, walk-through call
  Launch gate: [What must be true for Week 4 launch to proceed]
```

---

### Section 6 — Client Redirect Script

> **Load `references/redirect-scripts-library.md` now.** Identify the script that most closely matches the situation, adapt it to the client's specific numbers and context, and use it as the basis for this section. Do not copy verbatim — the PM needs to feel it is their own voice.

Write the exact words the PM should use if they need to redirect the client away from their stated ask toward the root cause fix. The script must:
1. Validate the stated pain — never dismiss what the client said
2. Name the root cause in business language, not technical language
3. Explain why addressing it first produces a better outcome for them
4. Offer a clear choice (not an open question)
5. Stay under 90 seconds spoken — this is a redirecting moment in a conversation, not a presentation

**Format:**
```
CLIENT REDIRECT SCRIPT
"[Full script, written to be spoken word-for-word or closely paraphrased.
Approximately 100–150 words. Present tense, direct, warm but confident.]"

What to listen for (client objections and how to handle):
• If they say "[likely objection]": "[response]"
• If they say "[likely objection]": "[response]"
```

---

## Worked Example

**Input provided to Claude:**

> Client brief from Heliocore (Series A, renewable energy, Germany, ~20 staff):
> "We have 200–300 leads a month coming in from trade shows and referrals. Only about 40% end up in Pipedrive, and our sales team says they spend too much time manually scoring. We want to build an automated scoring system that pushes qualified leads into Pipedrive."

**Output Claude produces:**

---

**STATED ASK**
Primary: "Build an automated scoring system that pushes qualified leads into Pipedrive."

---

**ROOT CAUSE SIGNALS**
• 60% of leads never reach Pipedrive — this is the primary loss point, and it occurs *before* scoring. The scoring problem can only affect the 40% that make it in. — Confidence: High (client stated the number)
• No deduplication or intake standardisation mentioned — trade show and referral leads likely arrive in inconsistent formats, names, and channels. Without normalization, a scoring model has nothing reliable to score. — Confidence: Medium (common pattern, not confirmed)
• "Sales team spends too much time manually scoring" — this is a consequence of volume + no triage, not a model problem. Adding an automated scoring layer without fixing intake leaves the manual triage step intact. — Confidence: Medium

Working hypothesis: The bottleneck is lead intake and deduplication — 60% of leads are being lost or left in a holding state before they reach the CRM, which means the scoring model has less than half the data to work with. Fixing intake first recovers more leads than any scoring improvement could.

---

**QUANTIFIED OPPORTUNITY**
If intake + deduplication is fixed: recovering 60% of leads entering Pipedrive means the team is working from a complete dataset. Assuming their current close rate holds, recovering 60% of previously-lost leads could represent 2–3x more qualified pipeline from the same volume.
Confidence: Medium
Basis: Client-provided number (60% not reaching Pipedrive); close rate not confirmed, assumed proportional.

If stated ask is implemented without addressing intake:
Automated scoring will perform well for 40% of leads. The 60% that never enter the system remain manual, missing, or duplicated. The team will likely report that the scoring "isn't working" because the pipeline volume doesn't noticeably change.

---

**MISSING INFORMATION**
| What We Need | Why It Matters | Question to Ask |
|---|---|---|
| Current lead intake method | Tells us where the 60% loss is happening | "When a lead comes in from a trade show, what's the first thing someone does with it — email, spreadsheet, direct Pipedrive entry?" |
| Pipedrive field requirements | Determines what enrichment is actually needed | "What fields does your sales team need populated before a lead is useful to them in Pipedrive?" |
| Current close rate from existing Pipedrive leads | Lets us quantify the revenue opportunity of recovering more leads | "Do you have a rough sense of what percentage of leads that enter Pipedrive become customers?" |
| Who currently handles manual scoring | Tells us whose time is actually being spent | "Is the manual scoring done by the sales team, or by someone else before it reaches them?" |

---

**PROPOSED 4-WEEK PLAN**

Week 1 — Intake Audit & Architecture
  Goal: Confirm exactly where the 60% lead loss is happening and design the intake flow
  Key tasks: Map current lead journey end-to-end; sample 50 recent leads to identify format patterns; design Google Sheet → n8n intake schema
  Dependencies from client: Google Sheet access or export of last 3 months of leads; 1-hour process walk-through with sales ops contact

Week 2 — Intake Flow + Deduplication
  Goal: Leads from all sources entering a single normalised intake sheet, with duplicates caught before Pipedrive push
  Key tasks: Build n8n intake flow; implement fuzzy deduplication (company + contact level); route clean leads to enrichment queue
  Dependencies from client: Confirm deduplication tolerance (should "SWM" and "Stadtwerke München" be treated as the same company?)

Week 3 — Enrichment + Scoring + CRM Push
  Goal: Qualified leads automatically pushed to Pipedrive with enrichment data populated
  Key tasks: Integrate enrichment API (mock if credentials delayed); implement scoring model against confirmed Pipedrive field requirements; test with 30 real leads from Week 1 sample
  Dependencies from client: Pipedrive API credentials; enrichment API credentials (Clearbit or equivalent)

Week 4 — Handoff & Launch
  Goal: Client can monitor and operate the system without PM involvement
  Key tasks: Handoff documentation; 5-minute Loom walkthrough; 30-min client walk-through call; go live on full volume
  Launch gate: 3 consecutive clean test runs with no unhandled errors

---

**CLIENT REDIRECT SCRIPT**

"You're completely right that scoring is where the sales team is losing time — that's the symptom we need to fix. What the data suggests is that the bigger problem is happening one step earlier: 60% of your leads are never making it into Pipedrive at all, which means the scoring model only ever sees 40% of your pipeline.

If we build scoring first, it'll work well for the leads already in the system, but the volume problem stays the same. If we fix intake and deduplication first — so every lead lands in Pipedrive, deduplicated and normalised — then scoring works on your full pipeline and the sales team stops doing triage manually.

I'd like to propose we spend the first two weeks on intake and have scoring live by Week 3. Same launch date, better outcome. Does that work for you?"

What to listen for:
• If they say "the scoring is more urgent because a demo is coming up": "Understood — we can stand up a basic scoring pass on the existing 40% within a week while the intake build runs in parallel. Which leads do you need scored by the demo?"
• If they say "we've tried fixing intake before and it didn't stick": "What specifically broke? That'll tell us whether it's a tool problem we can solve in n8n, or a process adoption problem we'd need to design around."

---

---

## Output Asset

After completing all six sections, tell the PM:

> "The full diagnosis is above. If you'd like a clean version to copy into Google Docs for review or client sharing, load `assets/diagnosis-memo-template.md` — it maps directly to the six sections above with version history and a decision log already built in."

Do not generate the template output automatically. The PM may want to edit the diagnosis first.

---

## When Not to Use This Skill

- The scope is already signed and the team is building — use SOP-002 (Handoff) or SOP-004 (Blocker Escalation) instead
- The user is asking a purely technical question about n8n, APIs, or implementation details with no client relationship context
- The user wants to generate a proposal document — this skill produces a working diagnosis, not a formatted proposal

## Output Length

Expect the full output to be 500–900 words. Shorter if the input is minimal (flag assumptions clearly). Do not pad. Do not summarise at the end — the PM knows what they just read.
