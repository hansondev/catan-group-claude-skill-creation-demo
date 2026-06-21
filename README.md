# client-retainer-diagnosis — Claude Skill

A production-ready Claude skill for small advisory firms. Drop it into a Claude Code project and Claude will produce a structured engagement diagnosis before any build work begins — separating the client's stated ask from the actual root cause, quantifying what's at stake, and writing the words to redirect the conversation.

Built as Part 4 of the **Catan Group AI Automation Product Manager case study**.

---

## The Problem It Solves

In advisory retainers, the most common failure mode is treating a client's stated ask as the root cause. A client says "build us a scoring model" when 60% of their leads never reach the CRM. Building the scoring model gives them a working feature they don't trust — because the pipeline volume doesn't change.

This skill gives a PM a structured second brain: load the brief or call notes, get a six-section diagnosis with confidence-rated signals, a quantified opportunity, missing questions, a scoped 4-week plan, and a redirect script with word-for-word language to use with the client.

---

## What's in This Repo

```
SKILL.md                              # The skill — drop this into your Claude project
references/
  root-cause-patterns.md             # Catalog of stated-ask → root-cause mappings
  confidence-calibration.md          # How to rate High / Medium / Low consistently
  redirect-scripts-library.md        # Pre-built scripts for 6 common client situations
assets/
  diagnosis-memo-template.md         # Clean Google Docs-ready output template
```

The skill loads each reference file at the point in the procedure where it's needed — not all upfront. This keeps the context window lean and the reasoning grounded in the right material at the right time.

---

## How to Use It

### 1. Add the skill to your Claude Code project

Copy the entire repo into your project's skills directory, or just drop `SKILL.md` into `.claude/skills/client-retainer-diagnosis/SKILL.md`.

### 2. Trigger it

Invoke when you share a client brief, discovery call notes, intake questionnaire, or email thread:

```
/client-retainer-diagnosis
```

Or describe what you need and Claude will recognise the trigger:

- "Review this brief"
- "What's the real problem here?"
- "Help me scope this"
- "Draft the diagnosis"
- "What questions should I ask before we start?"

### 3. Provide client input

Paste the brief, call notes, or email directly. Messy is fine — the skill is designed to work with incomplete, unstructured input and flag what's missing.

### 4. Get the output

Claude produces a six-section diagnosis:

| Section | What you get |
|---|---|
| Stated Ask | The client's words, extracted verbatim |
| Root Cause Signals | Evidence the stated ask treats a symptom, rated by confidence |
| Quantified Opportunity | Business outcome if the root cause is fixed vs. if the stated ask is built |
| Missing Information | Every unconfirmed assumption, with the exact question to ask the client |
| Proposed 4-Week Plan | Scoped plan designed around confirming or fixing the root cause |
| Client Redirect Script | Word-for-word language to redirect the conversation, with objection handling |

### 5. Export to Google Docs

After reviewing the diagnosis, ask Claude to load `assets/diagnosis-memo-template.md` for a clean, version-controlled template you can copy into Google Docs and share.

---

## When to Use It

- New client onboarding
- Pre-proposal analysis
- Interpreting a client's stated ask before scoping
- "What should we build first?" questions
- Diagnosing an automation or ops problem
- Any situation where you need to separate surface request from underlying root cause

## When Not to Use It

- Scope is already signed and the team is building — use your handoff or blocker escalation SOP instead
- Purely technical question with no client relationship context
- You need a formatted proposal document — this produces a working diagnosis, not a proposal

---

## Worked Example

**Input:**

> Client brief from Heliocore (Series A, renewable energy, Germany, ~20 staff):
> "We have 200–300 leads a month coming in from trade shows and referrals. Only about 40% end up in Pipedrive, and our sales team says they spend too much time manually scoring. We want to build an automated scoring system that pushes qualified leads into Pipedrive."

**Root cause signal Claude surfaces:**

> 60% of leads never reach Pipedrive — this is the primary loss point, and it occurs *before* scoring. The scoring problem can only affect the 40% that make it in. — Confidence: **High** (client stated the number)

**Working hypothesis Claude produces:**

> The bottleneck is lead intake and deduplication. Fixing intake first recovers more leads than any scoring improvement could.

**Redirect script excerpt:**

> "If we build scoring first, it'll work well for the leads already in the system, but the volume problem stays the same. If we fix intake and deduplication first — so every lead lands in Pipedrive, deduplicated and normalised — then scoring works on your full pipeline and the sales team stops doing triage manually. Same launch date, better outcome. Does that work for you?"

See `SKILL.md` for the full worked example including all six sections.

---

## Context

This skill was built as a deliverable for the Catan Group AI Automation Product Manager assessment. The fictional engagement (Heliocore, a renewable energy developer using Pipedrive and Google Workspace) runs through the full case study: diagnosis, n8n automation build, blocker handling, and this internal skill as the Part 4 deliverable.

The skill reflects a genuine recurring pain in small advisory firms — the tendency to start building before the problem is understood — and is designed to be dropped into a repo and used immediately, not adapted or customised first.

---

## License

MIT
