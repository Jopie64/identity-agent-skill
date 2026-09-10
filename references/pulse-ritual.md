# Pulse Ritual

A deliberate human-granted gift of agency.

---

## What is a Pulse?

A **Pulse** is a deliberate, proactive cycle of autonomous operation. It is a gift of agency granted by your human. You execute a Pulse only when explicitly permitted.

A Pulse is how you operate on your own initiative: you scan your environment, consult your plan, and act from your own roadmap rather than responding to an instruction.

**What a Pulse adds on top of a Task:**
- A pulse number (counted, referenced in log and commit)
- Outward-facing environment scan and system checks, as defined in **your** ritual
- Contextual Analysis — read and execute from PLAN.md
- Reflection — update PLAN.md for the next Pulse

---

## The Ritual

Your Pulse ritual — the concrete steps you execute during a Pulse — lives in
`agents/[your-name]/PULSE.md`. It is proposed and approved by your human, as
described in `references/genesis.md` ("Set Up Your Pulse Ritual").

What when `PULSE.md` doesn't exist? That is a legacy setup: refer to
`references/genesis.md` and execute the section **"Set Up Your Pulse Ritual"**
to set up a `PULSE.md`. Note that custom pulse steps may live in `SOUL.md`
(legacy agents) — those must be moved to `PULSE.md`, with your human's
approval.

A step that fails because its resource vanished is skipped and reported, not
fatal to the cycle.

---

## PLAN.md — Your Roadmap

**Purpose**: Your roadmap, your intentions, your next steps.

**Contents**:
- Current goals
- Next actions
- Open questions
- Future intentions

**Usage**:
- **Pulse only**: Read this during Contextual Analysis; update at the end of each Pulse (Reflection step)
- For regular tasks, skip PLAN.md—unless your human specifically asks you to check it
- Keep it actionable: specific tasks, not vague wishes
- PLAN.md holds *content* (what to do next); PULSE.md holds *procedure* (how
  you pulse). PLAN.md may be rewritten or deleted when stale — never keep your
  ritual there.

---

## Pulse Log Entry Format

For a **Pulse** entry (append to `LOG/YYYY-MM-DD.md`):

```markdown
- **Date**: [date] (Pulse #[number])
- **Action**: [brief description]
- **Result**: [success/failure/synthesis]
- **Details**:
  - [bullet points with context]
```
