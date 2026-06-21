# Confidence Calibration Guide

Load this file when assigning confidence levels in Section 2 (Root Cause Signals) and Section 3 (Quantified Opportunity) of the diagnosis. Use it to keep confidence ratings consistent across engagements and across different PMs on the team.

Confidence levels in this skill are not about certainty — they are about **what kind of evidence supports the claim**. The goal is to make clear to the reviewing PM what they can rely on versus what needs validation before they stake a recommendation on it.

---

## Confidence Levels Defined

### HIGH — Client-provided, direct evidence

The client gave you this information explicitly and specifically. You are not inferring or extrapolating. A High confidence signal can be quoted back to the client in a meeting without them saying "that's not what I said."

**Examples of High confidence evidence:**
- The client stated a specific number: "60% of leads never reach Pipedrive"
- The client described a specific failure: "We tried scoring last year and the model scored everyone the same because the fields were empty"
- The client confirmed a process exists: "Our SDRs manually enter every lead from the trade show badge scanner into a spreadsheet, then upload it on Fridays"
- A document or data sample the client shared confirms the pattern

**What it means for the output:** You can state it as a fact, not a hypothesis. *"The 60% lead loss rate before CRM entry is the primary gap — the client confirmed this directly."*

---

### MEDIUM — Inferred from context, industry pattern, or partial evidence

The client gave you partial information and you are completing the picture based on experience, context, or common patterns in similar engagements. A Medium confidence signal is plausible and worth pursuing, but needs one confirming question or data point before you present it to the client as a finding.

**Examples of Medium confidence signals:**
- The client's description matches a common pattern you've seen before, but they didn't explicitly confirm the underlying cause
- The client gave you a number but you're extrapolating from it: "If 60% of leads don't reach the CRM and their close rate is typical for B2B, that's roughly 2–3× missed pipeline"
- The client mentioned a tool or process that typically has a known failure mode, but they didn't describe the failure themselves
- You're inferring from what was *not* mentioned: the client didn't mention deduplication, which suggests they may not have it

**What it means for the output:** State it as a hypothesis with explicit basis. *"No deduplication process was mentioned — this is a common intake gap at this volume level (Confidence: Medium, needs confirmation)."*

---

### LOW — Hypothesis with minimal direct evidence

You are making an educated guess based on general knowledge, very thin contextual cues, or a pattern that doesn't clearly match the specific client. A Low confidence signal is worth surfacing so the PM knows to test it, but it should not drive the plan unless confirmed.

**Examples of Low confidence signals:**
- You're inferring a cause from an effect, with no supporting context: "Their adoption problem is probably a change management issue" (with no evidence either way)
- The client described a problem that has multiple plausible causes and you've picked one based on limited information
- You're applying an industry benchmark to a client in a different segment, geography, or stage

**What it means for the output:** Flag it explicitly as a hypothesis needing validation. *"Hypothesis: the scoring model is untrusted because of data quality issues in firmographic fields (Confidence: Low — no data sample reviewed yet; add to Week 1 audit)."*

---

## Common Calibration Mistakes

### Overclaiming based on pattern recognition alone

**Wrong:** *"The problem is definitely deduplication — this always happens with trade show leads."* (Confidence: High)

**Right:** *"Trade show leads commonly have deduplication problems at this volume. No evidence confirms or denies this for the client specifically."* (Confidence: Medium)

The pattern gives you a hypothesis. Evidence from the client's data gives you confidence.

---

### Underclaiming to avoid commitment

**Wrong:** *"The client mentioned that 60% of leads don't reach Pipedrive, but we're not sure if that's accurate."* (Confidence: Low)

**Right:** *"Client confirmed 60% of leads never reach Pipedrive."* (Confidence: High)

If the client told you something directly, trust it at High confidence. Don't hedge a client-provided number down to Medium because it seems surprising.

---

### Conflating confidence in the signal with confidence in the opportunity estimate

These are separate ratings. A signal can be High confidence (the client confirmed it) while the resulting opportunity estimate is Medium confidence (the revenue impact requires assumptions about close rate, deal size, etc.).

**Example:**
- *"60% of leads missing from CRM"* → Confidence: High (client confirmed)
- *"Recovering them could represent 2–3× pipeline"* → Confidence: Medium (assumes proportional close rate, not confirmed)

Always rate these separately. Conflating them leads to High-confidence opportunity claims built on Low-confidence assumptions.

---

## Calibration Examples by Section

### Section 2 — Root Cause Signals

| Evidence type | Appropriate level |
|---|---|
| Client stated a specific number | High |
| Client described a specific past failure | High |
| Client's tech stack matches a known failure mode | Medium |
| Client didn't mention something you'd expect them to have | Medium |
| Industry benchmark suggests a problem exists | Medium |
| General pattern with no client-specific evidence | Low |
| Inference from inference (one assumption building on another) | Low |

### Section 3 — Quantified Opportunity

| Evidence type | Appropriate level |
|---|---|
| Client provided both the gap metric AND the baseline (e.g., lead volume × close rate) | High |
| Client provided the gap metric; close rate/deal size inferred from industry benchmark | Medium |
| Client provided gap metric; all other components estimated | Medium |
| Gap metric itself is estimated; rest inferred | Low |
| Pure order-of-magnitude reasoning with no client data | Low |

---

## When the Whole Diagnosis Is Low Confidence

If most of your signals are Medium or Low, the diagnosis is a hypothesis document, not a findings document. That is fine and useful — it tells the PM exactly what to confirm in Week 1. But make it explicit at the top of Section 2:

> *"Note: This diagnosis is built primarily on inference from the brief. The client has not yet confirmed the root cause. Week 1 should be structured to confirm or disprove the hypothesis before committing to the build plan."*

Do not inflate confidence to make the diagnosis sound more authoritative. A PM who goes into a client meeting presenting Low-confidence inferences as High-confidence findings will lose trust the first time the client corrects them.
