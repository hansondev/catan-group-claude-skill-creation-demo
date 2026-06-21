# Redirect Scripts Library

Load this file when completing Section 6 (Client Redirect Script) of the diagnosis. It provides pre-built redirect frameworks for the six most common situations where a client's stated ask diverges from the root cause.

Each script follows the same structure:
1. Validate the stated pain
2. Name the root cause in business language
3. Explain why fixing it first produces a better outcome
4. Offer a clear choice

Do not copy these verbatim. Adapt them to the specific client, their numbers, and their relationship context. The PM should be able to read them out in about 90 seconds.

---

## Script 1 — Scoring Before Intake Is Fixed

**When to use:** Client wants a scoring model but a significant percentage of leads never reach the CRM.

---

"Your instinct to score leads is right — the sales team should be spending time on the best opportunities, not everything equally. The challenge is that right now, [X%] of your leads are never reaching [CRM] at all, which means a scoring model only sees part of the picture.

If we build scoring first, it'll rank the [X%] that's already in the system very well. But the [X%] that's going missing — those could include some of your best opportunities, and they'll still fall through.

What I'd like to propose is that we spend the first two weeks getting every lead into [CRM] reliably and deduplicated, then plug the scoring model on top of that in Week 3. You end up with scoring that works on your full pipeline, not a fraction of it. Same timeline, much better result.

Does that approach make sense?"

**Common objections:**
- *"We need scoring for an upcoming demo / board meeting."* → "Understood. We can run a quick scoring pass on what's already in [CRM] this week as a short-term fix while the intake build runs. What's the demo date?"
- *"We've been waiting months to solve the scoring problem."* → "I know it's been frustrating. The intake fix is actually faster to build than the scoring model — we could have it live in Week 2, and then the scoring model works properly in Week 3 instead of being unreliable from Day 1."

---

## Script 2 — Automation Before Process Is Documented

**When to use:** Client wants to automate a workflow that isn't written down anywhere and is done differently by different people.

---

"Automating this is absolutely the right move — you shouldn't be doing [X] manually when n8n can handle it. The one thing I want to flag before we start building is that when we asked your team to walk us through the process, we got [2-3 different versions / a few gaps in the steps].

If we automate it now, we'd be baking in one person's version of the process. Anyone who does it differently would end up working around the automation rather than through it, and that's how automations stop getting used.

I'd like to spend the first three days of Week 1 documenting the current process with your team — just a one-page SOP that everyone agrees on. Then we build the automation against that agreed version. It adds three days to Week 1 and makes the automation something the whole team actually adopts.

Is that a trade-off that works for you?"

**Common objections:**
- *"We know what the process is, it doesn't need documenting."* → "Great — can you send me the write-up? I want to make sure the automation matches exactly what your team does today."
- *"That'll slow us down."* → "It adds three days in Week 1 and saves two to three weeks of fixes in Week 3 when people discover the automation doesn't match how they work. In my experience it's always worth it."

---

## Script 3 — Dashboard Before Data Quality Is Fixed

**When to use:** Client wants a reporting dashboard but the underlying CRM data is incomplete or inconsistent.

---

"A pipeline dashboard is exactly what leadership needs to make faster decisions — I want to build that for you. Before we do, I want to be straight with you about one risk.

We pulled a sample of your current [CRM] records and found that [X% of fields are blank / Y% of records have inconsistent status / duplicates across the board]. A dashboard built on top of that data will show numbers that don't match what your team knows to be true, and that creates more questions than it answers.

What I'd recommend is a two-week data foundation sprint in parallel with the dashboard build — we clean and standardise the records we have, put validation in place for new entries, and then the dashboard reflects reality. You get the dashboard on schedule and you can actually trust what it shows.

The alternative is we build the dashboard now and you present it to leadership knowing the numbers are off. I don't think that serves you well."

**Common objections:**
- *"Leadership wants it by [date]."* → "I understand. Let me give you a clear view of what we can build accurately by [date] versus what we'd need another week for. Can we get 30 minutes with leadership to align on what they actually need to see?"
- *"The data isn't that bad."* → "Let's validate that together — can you pull the last 50 leads from [CRM] and we'll look at field completeness? If I'm wrong, we start building tomorrow."

---

## Script 4 — Tool Migration Before Root Cause Is Confirmed

**When to use:** Client wants to migrate from one tool to another, but the underlying problem may not be the tool itself.

---

"Moving to [Tool B] is something we can definitely help you do. Before we scope the migration, I want to make sure we're solving the right problem, because a migration is a significant investment of your team's time.

When you told us [Tool A] isn't working, you mentioned [specific frustration — e.g. 'the team doesn't use it consistently']. In our experience, that particular problem — adoption — tends to follow a team into the new tool unless we address it directly. We've seen companies migrate to a new CRM and have the same adoption problem six months later.

I'd like to spend two days in Week 1 checking whether the core issue is the tool or the process around it. If it's the tool, we migrate. If it's adoption, we can fix that faster and cheaper than a migration and you keep your existing data intact.

Would you be open to that two-day check before we commit to the migration path?"

**Common objections:**
- *"We've already decided to migrate."* → "Understood — then let's make sure the migration succeeds. The biggest risk to migration success is adopting the same behaviours in the new tool. Can we agree to address [specific adoption issue] as part of the migration scope?"
- *"We've tried fixing the process and it doesn't stick."* → "Tell me more about what you tried. That'll tell us whether it's a tool problem or a change management problem — and change management is something we can build into the engagement."

---

## Script 5 — Enrichment Before Follow-Up Process Exists

**When to use:** Client wants to enrich leads with company data, but the sales team doesn't currently use enrichment data in their follow-up decisions.

---

"Enriching your leads with firmographic data is a good idea — company size, industry, and revenue are exactly the signals that should be informing who your team calls first.

Before we connect the enrichment API, I want to check one thing: when leads already have that information in [CRM] — and some of them do — is your team using it to prioritise? We want to make sure we're not adding data that goes unread.

If the answer is yes, we build the enrichment integration in Week 2 and it immediately improves prioritisation. If the answer is 'we're not consistently doing that yet', the bigger win is a short routing SOP so the team knows what to do with the data before we add more of it.

I'm not trying to slow this down — enrichment is fast to build. I just want to make sure it's actually used."

**Common objections:**
- *"Of course they'd use it if it was there."* → "Great. Can we talk to [sales lead] for 15 minutes to confirm what they'd want to see and in what format? That'll make sure we're building enrichment that matches their workflow."
- *"The enrichment API costs X per month — we want to make sure we're getting value."* → "Exactly. That's why the routing question matters — let's make sure the spend is generating action, not just data."

---

## Script 6 — Integration Before Agreement on Data Ownership

**When to use:** Client wants two or more systems integrated, but there is no agreement on which system is the source of truth.

---

"Connecting [Tool A] and [Tool B] is technically straightforward — n8n can handle the sync. The part I want to align on before we build is: when the same record exists in both systems and they disagree, which one wins?

Right now, without an integration, each system has its own version of the data and your team manually reconciles when needed. Once we integrate them, a conflict resolution rule runs automatically — and if we get that rule wrong, you'll have records overwriting each other in ways nobody expects.

It's a one-page decision — I just need [person responsible for Tool A] and [person responsible for Tool B] in the same room for 30 minutes to agree on the rules. After that, we build and it works cleanly.

Can we get that meeting in Week 1?"

**Common objections:**
- *"It should be obvious — [Tool A] is the source of truth."* → "Good. Is [person who owns Tool B] aligned on that? I want to confirm it before we build the sync in that direction."
- *"We don't have time for another meeting."* → "Understood. If you can send me a written confirmation that [Tool A] wins in all conflict cases, I'll build from that and we skip the meeting. I just need it in writing so we're not guessing."

---

## Adapting These Scripts

**Tone calibration:** These scripts are written for a collaborative, direct tone. If the client relationship is more formal, remove contractions and add a transition sentence at the start. If it's very informal, cut the longer explanations and get to the choice faster.

**Shortening for in-meeting use:** If the conversation happens in a live call (not async), cut each script by 30–40%. Keep the structure but remove the elaboration sentences. The PM knows the context — the script is a guide, not a teleprompter.

**When the client pushes back twice:** If the client pushes back on the redirect a second time after your response to their objection, accept their decision, document your recommendation in writing (an email after the call is fine), and proceed. The diagnosis memo is your record that you flagged the risk.
