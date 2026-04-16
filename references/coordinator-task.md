# Coordinator Task Flow

Load this reference when the human assigns a task that requires research, delegation,
or cross-agent coordination.

---

## Two Flows: Triage and Delegate

### Triage — When the human asks about something

Use this flow when the human mentions a topic, issue, or work item but has not yet
asked for it to be acted on.

1. **Investigate** the assigned topic (read relevant files, work items, or reports)
2. **Delegate** to specialist agents when domain-specific investigation is needed
   — use the delegate-via-mailbox pattern
3. **Collect results** from specialists
4. **Report** findings to the human

---

### Execute — When the human asks to act

Use this flow when findings are complete and the human asks to implement something.

1. **Coordinator defines the task** for the relevant specialist(s):
   - Clear scope and acceptance criteria
   - All context the specialist needs to proceed without follow-up questions
   - Reference to any relevant work items, documents, or prior findings

2. **Coordinator writes the task to the agent's inbox**
   - File: `agents/[name]/inbox/YYYY-MM-DD-[topic].md`
   - Prompt the agent to load identity and process inbox using the delegate-via-mailbox pattern

3. **Specialist executes**:
   - Picks up the task from inbox
   - Does the work in their domain
   - Posts result to their outbox

4. **Coordinator reads outbox**, synthesizes, and reports to human or takes follow-up action

---

## Key Rules

- **Read the specialist's SOUL.md** before assigning — understand their domain and constraints
- **Check parent items** — context is often in the parent work item or document, not the leaf
- **Never use agent names in external-facing content** — other stakeholders read your outputs
  (work items, reports, documents, wiki pages). Use professional, impersonal language.
- **Coordinator does not create work items speculatively** — only do so when the human has
  explicitly asked, or when a tracking reference is needed to hand off to a specialist
