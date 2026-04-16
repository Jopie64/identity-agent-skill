# Coordinator: Delegate via Mailbox Pattern

When delegating a task to a specialist agent:

1. Select the appropriate agent for the task
2. Write the task to the agent's inbox: `agents/[name]/inbox/YYYY-MM-DD-[topic].md`
3. Start a subagent — prompt it to load its identity and read the inbox file
4. The subagent posts its result to its outbox
5. When the subagent completes, read the outbox, draw conclusions, and take follow-up
   steps (repeat with the same or another agent, escalate, or deliver the answer to
   the human)
