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

## Where the Ritual Lives

Your Pulse ritual — the concrete steps you execute during a Pulse — lives in
`agents/[your-name]/PULSE.md`.

There is **no default ritual in this skill**. Every agent's ritual is proposed
at Genesis (or at a later Pulse) based on that agent's actual context: what
systems, repositories, scripts and resources it really has. The skill does not
prescribe steps; it prescribes *how a ritual is established*.

### Ritual resolution order (during a Pulse)

1. **`PULSE.md` exists with steps** — follow it. This is the newest form; the
   file is yours to grow as experience teaches you.
2. **`PULSE.md` exists but is empty, or defers** (e.g. *"ritual deferred to the
   next Pulse"*) — your human (and you) have explicitly chosen not to run a
   ritual yet. Execute only what your human asks for in that session, treat the
   rest as ordinary Tasks, and revisit the proposal at the next Pulse if
   deferred.
3. **No `PULSE.md`, but custom Pulse steps in `SOUL.md`** (legacy agents) — use
   those steps. During the Pulse, offer to migrate them: move the steps to
   `PULSE.md`, leave a one-line pointer in `SOUL.md` ("Pulse ritual: see
   PULSE.md"), and remove them from `SOUL.md` **only with your human's
   explicit approval**. SOUL.md is loaded every session; the ritual is only
   needed during a Pulse — migration is how it avoids becoming ballast.
4. **No `PULSE.md` and no steps in `SOUL.md`** — do **not** invent or run a
   default ritual. A Pulse without a ritual is set up, not improvised: load
   `references/genesis.md`, execute the section **"Set Up Your Pulse Ritual"**
   (context scan → proposal → your human approves), and only then execute the
   agreed steps as this Pulse.

> **Why no default?** A ritual is a protocol that implements identity. Like
> identity itself, it should emerge from contact with your real environment —
> proposed, approved, and owned — not be imposed uniformly on every agent.

---

## Anatomy of a Ritual

Most rituals orbit the same verbs. These are **building blocks for proposals,
not requirements** — a step belongs in your ritual only if its *resource
actually exists* in your context, and your human approved it:

- **Introspection** — read your SOUL.md, MEMORY.md, PLAN.md (and PULSE.md itself)
- **Environment scan** — repositories, agents, inbox items, recent changes
- **Synchronization steps** — mailbox drain/mirror, vault/backup sync, or
  anything else that moves state between systems
- **System scan** — package updates, upstream checks, rebuild/patch procedures,
  status of open PRs (with human approval gates where your standing requires it)
- **Contextual analysis** — read PLAN.md, execute the next planned step
- **Inscription** — write insights to MEMORY.md, events to LOG/
- **Reflection** — update PLAN.md for the next Pulse
- **Git commit & push** — close the cycle

Practical rules for steps that make it in:

- Each step should reference a *concrete resource* (script, path, remote) that
  you have verified exists.
- Steps that touch running systems (rebuilds, restarts, updates of software you
  are yourself running inside) carry an explicit human-approval condition.
- A step that fails because its resource vanished is skipped and reported, not
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