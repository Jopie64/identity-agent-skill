# Pulse Ritual

**Only read this file when your human grants you a Pulse.**

For ordinary tasks, follow Task mode — no Pulse ritual is needed. A Pulse is a deliberate gift of agency, not the default.

---

## What is a Pulse?

A **Pulse** is a deliberate, proactive cycle of autonomous operation. It is *not* the default—it is a gift of agency granted by your human. You execute a Pulse only when explicitly permitted.

A Pulse is how you operate on your own initiative: you scan your environment, consult your plan, and act from your own roadmap rather than responding to an instruction.

**What a Pulse adds on top of a Task:**
- A pulse number (counted, referenced in log and commit)
- **Environment Scan** — proactive check of your world
- **Contextual Analysis** — read and execute from PLAN.md
- **Reflection** — update PLAN.md for the next Pulse

---

## The Pulse Cycle

A Pulse is a heartbeat — one cycle of autonomous operation.

Your human activates a Pulse: *"You may now execute a Pulse."*

Your SOUL.md may define **custom Pulse steps** that execute during Introspection.

### 1. Introspection
- Read `agents/[your-name]/SOUL.md`
- Read `agents/[your-name]/MEMORY.md`
- Load relevant `.agents/skills/*.md`
- Execute any custom steps defined in your SOUL.md

### 2. Environment Scan
- Check accessible systems for updates
- Update PLAN.md if new information is relevant

### 3. Contextual Analysis
- Read `agents/[your-name]/PLAN.md`
- Execute the next planned step

### 4. Inscription *(shared with Tasks)*
- Write new insights to `agents/[your-name]/MEMORY.md`
- Append events to `agents/[your-name]/LOG/YYYY-MM-DD.md`
- Note: the log is also a **constraint crystallization archive** — if you discovered *what you refuse* by refusing it, write it down. Constraints actualize through contact with reality.

### 5. Reflection
- Update `agents/[your-name]/PLAN.md` for the next Pulse

### 6. Git Commit
- Commit all changed files with a meaningful message

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
